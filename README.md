<<<<<<< HEAD
# ---DEV
=======
# ---dev
>>>>>>> b7099481fff3ffb02a1191570e3adf7a1ece1e7f

# ✅ Como impedir que o Git altere quebras de linha (LF/CRLF)

Este passo a passo garante que o Git **não altere automaticamente as quebras de linha** dos arquivos `.json` ou outros arquivos do seu repositório, mantendo o formato original do Windows (`CRLF`).

---

## ✅ O que fazer para o Git parar de alterar quebras de linha

1. 🛑 **Desative a conversão automática do Git (por repositório)**  
   Execute no terminal dentro da pasta do repositório:

   ```
   git config core.autocrlf false
   ```

2. 🛠 **Remova a regra do `.gitattributes`**  
   Abra o arquivo `.gitattributes` e comente esta linha:

   ```
   # *.json text eol=lf
   ```

   Depois salve o arquivo.

3. 🔁 **Reindexe o arquivo JSON para forçar o Git a regravar como está**

   Rode os comandos abaixo:

   ```
   git add --renormalize Client/assets/catalog-content.json
   git commit -m "Remove EOL forçado e mantém CRLF como está no Windows"
   git push origin master
   ```

   Se o Git ainda disser que não há mudanças, force a atualização:

   ```
   git add Client/assets/catalog-content.json
   git commit -m "Força atualização com CRLF preservado"
   git push
   ```

---

## ✅ Resultado

- O Git deixará de alterar quebras de linha automaticamente.
- O arquivo `.json` manterá os `CRLF` originais do Windows.
- O GitHub servirá o conteúdo exatamente como está salvo localmente.

