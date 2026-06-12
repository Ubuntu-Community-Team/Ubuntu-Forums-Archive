---
title: "Recovery mode y must be setuid root"
date: 2010-06-27
forum: Software
---

### Post by akiestudio on 2010-06-27
Hola buenas a todos, tengo  el siguiente problema.
Hice un Chmod 777 -R /usr, y ahora me sale lo de must be a setuid root cada vez que intento un sudo , he leido por ahi que deberia de entrar en recovery mode para poder modificar el root y que no sucediera mas ese problema, pero resulta que cuando entro en recovery mode sale lo siguiente.
Ext3 -fs
begin:running/script/local-bottom...
done
begin:running/script/init-bottom...
done
y hay se queda la pantalla en negro...y no sale mas , ni un terminal ni nada, como puedo hacer para solucionar lo de root .

Gracias

---

### Post by quixote on 2010-06-29
I don't speak Spanish too well, so I hope someone else will confirm or fix my understanding of this.  If you changed the /usr permissions to 777 that could break all sorts of permissions only root is supposed to have.  (You probably don't need me to tell you at this point: Don't do that! :D)  

I would try two things. 
1) fix the permissions on /usr. Boot with a livecd, mount the partition with /usr on it.  You could go to Places > Home which opens the nautilus file manager.  In the left hand pane which probably has "Places" at the top, click on the [???]GB Filesystem which seems about the right size for your root partition.  That will mount it, and you can also look to make sure /usr is there. Note the location in the bar above the main right pane that will say something like /media/some-endless-uuid-number.  (Tip for later: you can select and copy the uuid, then paste it into the terminal where you need it using ctrl-**shift**-v.)

Open a terminal (Applications > Accessories > Terminal) and type this command to change files to 644 permissions:```
sudo find /media/*uuid-number*/usr -type f -exec chmod 644 {} \;
```
then change directories to 755 permissions:```
sudo find /media/*uuid-number*/usr -type d -exec chmod 755 {} \;
```
Check to make sure that the /usr directory itself is now 755.  If not "sudo chmod 755 /media/*uuid-number*/usr" (without quotes) will take care of it.

And now keep your fingers crossed and try booting without the livecd

2) if that doesn't work, we'll run visudo to fix the permissions for root.  I'll go through those steps if it looks like you need them.

---

### Post by alfplayer on 2010-06-30
**Traducción, por si es necesaria**

Yo no hablo español muy bien, así que espero que alguien más lo confirme o me corrija. Si ha cambiado los permisos de /usr a 777 eso podría romper todo tipo de permisos que sólo el usuario root se supone que tiene. (Es probable que no necesite que le diga en este momento: ¡No hagas eso!) 

Me gustaría intentar dos cosas. 
1) Arreglar los permisos en /usr. Arrancar con un livecd, montar la partición con /usr en él. Usted podría ir a Lugares > Inicio, que abre el gestor de archivos Nautilus. En el panel de la izquierda, que probablemente tiene "Lugares" en la parte superior, haga clic en "Soporte de [???] GB" que parece del tamaño adecuado para su partición raíz. Eso lo montará, y también puede consultar para asegurarse de que /usr está allí. Anote la ubicación en la barra superior del panel principal derecho que dirá algo como /media/código-sin-fin-uuid-separado-por-guiones. (Consejo para más tarde: se puede seleccionar y copiar el uuid, a continuación, pegarlo en la terminal donde usted lo necesite usando Ctrl-Shift-v.) 

Abre un terminal (Aplicaciones> Accesorios> Terminal) y escriba este comando para cambiar los permisos de archivos a 644: 
```
sudo find /media/*código uuid*/usr -type f -exec chmod 644 () \; 
```
a continuación, cambie los permisos de directorios a 755: 
```
sudo find /media/*código uuid*/usr -type d -exec chmod 755 () \; 
```
Asegúrese de que el directorio /usr en sí es ahora 755. Si no es "sudo chmod 755 /media/*código uuid*/usr" (sin comillas) se hará cargo de eso. 

Y ahora cruza los dedos y tratar de arrancar sin el livecd 

2) si eso no funciona, vamos a ejecutar visudo para arreglar los permisos para el usuario root. Seguiré esos pasos si parece que lo necesita.

---

### Post by akiestudio on 2010-06-30
Thank you very much, But Did Not works,...

If I type in terminal now: ls -l

drwxr-xr-x 16 root root usr

and also type sudo visudo and i got this,

 GNU nano 2.0.9          Fichero: /etc/sudoers.tmp                             

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
                               [ Leer 25 líneas ]
^G Ver ayuda ^O Guardar   ^R Leer Fich ^Y Pág Ant   ^K Cortar Tex^C Pos actual
^X Salir     ^J Justificar^W Dónde Está^V Pág Sig   ^U PegarTxt  ^T Ortografía

But I do not know what i have to do it here....can anyone help ? And sorry for my english.
I forgot to keep mine fingers crossed... do you think maybe did not works for it. ;-)

any help?

---

### Post by quixote on 2010-06-30
You got the permissions changed.  That's good.  You're at least half way there. 

Editing visudo involves doing exactly what you did:```
sudo visudo
```That uses a command-line editor called nano.  The arrow keys, and the back space key work so it's easier to move around and fix mistakes than in some of the earlier command-line editors.

Your sudoers file looks a bit odd.  Maybe the lines are just in a slightly different order, or maybe it got corrupted. (This is the [ubuntu page on sudoers]("https://help.ubuntu.com/community/Sudoers"). The relevant bit is near the end.)  Here's what the sudoers file should look like:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

[B]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/B]
```

You're either missing the bit in bold, or it's off the screen.  If missing, you need to put it in.  Use the down arrow to get the cursor to the end, type it in, hit Ctrl-x when you're done.  You'll be asked whether to save, and either type y or just hit return (I think yes is the default).  

Important: if there are error messages do *not* force close, pull the power plug, or do anything until it's fixed.  The visudo program checks for typos, and if there's anything wrong, it won't save.  This is necessary because a problem with basic permissions can -- well, you know this! -- make the system unusable.

Okay, now when you reboot, we can hope things will work.  If not, come back with what error messages you get and hopefully we'll be able to fix those.

(Oh, and keep your fingers crossed.  That's essential.  But not while typing. :biggrin:)

---

### Post by alfplayer on 2010-06-30
akiestudio: Pedí ayuda si no entendés lo que escribió quixote.

---

### Post by akiestudio on 2010-06-30
I start with the Live Cd , and I did the change,

%admin ALL=(ALL) ALL.

y restarted , but if i try sudo gedit A, same error:
 sudo: must be setuid root.

what i can do it?

---

