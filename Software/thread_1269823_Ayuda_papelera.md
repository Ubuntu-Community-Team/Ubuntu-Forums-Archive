---
title: "Ayuda papelera"
date: 2009-09-18
forum: Software
---

### Post by Fisaulerod on 2009-09-18
Resulta que me baje un juego, Cube 2, pero ahora decidí eliminarlo. La cuestión es que lo tenia en /usr/local/games y lo eliminé como root, pero luego viendo el espacio libre en disco me di cuenta que no se eliminó y se fue a la papelera. Bueno, entonces como root me voy a ./local/share/Trash/files/, y al eliminar algo como que se elimina y vuelve a aparecer. He hecho muchas cosas como:

sudo rm -rf ~/.local/share/Trash/files/*

y comandos parecidos, pero no resulta, no se eliminan...que puedo hacer? gracias de antemano.

---

### Post by EnriqueK on 2009-09-18
sudo rm -Rf /root/.local/share/Trash/files/*
sudo rm -Rf /root/.local/share/Trash/info/*

---

### Post by Fisaulerod on 2009-09-18
Gracias, ahora funciono :P.

---

