---
title: "Help with pakage"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by miguelpires on 2012-06-28
Last night I was upgrading my install and for some reason I don't pay much atention. Now I've this problem and I can't solved him:
miguel@miguel-Satellite-A660:~$ sudo apt-get -f install
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
A corrigir dependências... Feito
Os seguintes pacotes extra serão instalados:
  evince
Pacotes sugeridos:
  poppler-data
Serão actualizados os seguintes pacotes:
  evince
1 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 79 não actualizados.
1 pacotes não totalmente instalados ou removidos.
É necessário obter 0 B/210 kB de arquivos.
Após esta operação, serão utilizados 0 B adicionais de espaço em disco.
Deseja continuar [Y/n]? y
dpkg: problemas com dependências impedem a configuração de evince:
 evince depende de libevdocument3-4 (= 3.5.3-0ubuntu3); no entanto:
  A versão de libevdocument3-4 no sistema é 3.5.3-0ubuntu4.
 evince depende de libevview3-3 (= 3.5.3-0ubuntu3); no entanto:
  A versão de libevview3-3 no sistema é 3.5.3-0ubuntu4.
dpkg: erro ao processar evince (--configure):
 problemas com dependências - a deixar por configurar
Nenhum relatório apport escrito pois MaxReports já foi atingido
                                                               Foram encontrados erros enquanto processava:
 evince
E: Sub-process /usr/bin/dpkg returned an error code (1)
miguel@miguel-Satellite-A660:~$ 
Can abyone help me with this dependences?
Regard's
Miguel

---

### Post by cariboo on 2012-06-28
I had the same problem the day before yesterday, regular updates solved the problem.

---

### Post by miguelpires on 2012-06-28
> **cariboo907 said:**
> I had the same problem the day before yesterday, regular updates solved the problem.

The system don't let me update

---

### Post by IWantFroyo on 2012-06-28
> **miguelpires said:**
> The system don't let me update

What is the output of the update command?

```
sudo apt-get update
```

---

