---
title: "ubuntu as an application server - what way to go?"
date: 2009-04-29
forum: Server Platforms
---

### Post by pepeantonio1 on 2009-04-29
Hi there,
I recently joined this community and I'm already impressed with the help provided by Ubuntu supporters. Thank you very much!
I'm fairly new to Linux as well so please go easy on me. I've installed and used Ubuntu desktop and I recently installed a Hardy Server Edition to basically provide shares, shared printer capabilities and other centralized services like VPN and Web filtering.

Now I want to extend the capabilities of this installation by allowing Windows users (domain or not) to connect to the box using FreeNX or any other solution (I'm not attached to any) and let them run applications on the server such as GNUCash, Firefox, Evolution etc. 

Through reading a lot of posts I have got the impression that setting GUI on the server is not a good idea. Also it is confusing to me if by setting users and groups using eBox, those users will be able to log in to the Ubuntu server and run any of the mentioned applications.

So I think what I need is a little guidance from the experts on which way to go. Is it better to add GUI to the server so users can run installed applications or should I use for that purpose a full desktop install and beef it up with server capabilities? Or neither? In any case, how do the user's accounts must be set up to allow them to run the applications remotely and also have their application data saved in their home folders in the Linux box?

I don't really specifics instructions, just a little bit of guidance. My goal is to have an application server where more than 2 Windows users can log in and run those applications.

Thanks and keep the good work!!!
Pepe.

---

### Post by pepeantonio1 on 2009-05-01
OK, 
I think I'm better informed now but still I have some questions. The must important thing is to know what you want to achieve as this dictates the way to go. I have discovered that using a LTSP server will allow thin client PCs to run Ubuntu applications. The thin clients have to boot to a PXE environment and from there is all Ubuntu applications. But that is not exactly what I want. 

I want my existing Windows machines to be able to open terminal sessions with an Ubuntu server and run applications installed on this server. I want to do this for several reasons:
- We still need to run Windows applications on the PCs
- I want to introduce long time windows users to the world of Linux without installing it locally on their PCs and have them to do dual boot or install any virtual machine application
- I want to get a grasp of the process of how Linux handles config files and other user data when those users run applications remotely (where the data is saved and how Linux makes it private to the owner/user)
- I want to have the same set up as a normal Windows environment have, i.e. a bunch of win clients and a Win server with Terminal Services running some applications (please I understand the differences between only-Windows and a mixed environment, I just want to achieve the same idea using Linux as a server)


What I have learn:
 - Apparently the best way to run Ubuntu applications is using freeNX on the Ubuntu computer and installing a NX client on the Windows PCs (Nomachine NXClient seems to be the perfect candidate)

**What is NOT clear to me is:**
-What version of Ubuntu should I use. Is it Edubuntu, Ubuntu and then is it Desktop or Server or the Alternate install with LTSP? **I'm  CONFUSED**!! **PLEASE HELP** with this as I do have little time for this project and I don't want to take the wrong route.

Thanks,

---

### Post by HermanAB on 2009-05-01
Howdy, 

There are many old reasons why one should not run a GUI on a server.  Most of those reasons are now obsolete, because servers are fast and RAM is cheap.

If your server has a screen and keyboard attached, then by all means, install a GUI, but consider switching to runlevel 3.  When you need to do something GUIsh, run startx and when you are done, exit it.  That way, you have the best of both worlds.

---

### Post by R.Bucky on 2009-05-01
I would tend to disagree with the last post. If you have a server, one of the main concerns is security. Installing a GUI usually means that you are installing other programs that work with the GUI. The more programs that are installed, the more holes or potential entry points you create to your server.

---

### Post by techstop on 2009-05-02
> **R.Bucky said:**
> I would tend to disagree with the last post. If you have a server, one of the main concerns is security. Installing a GUI usually means that you are installing other programs that work with the GUI. The more programs that are installed, the more holes or potential entry points you create to your server.

Exactly. You want to minimise the potential for attackers to exploit vulnerabilities in your server. This means only installing the packages you need. A GUI is not necessary or recommended for a secure server.

---

### Post by koenn on 2009-05-02
> **R.Bucky said:**
> I would tend to disagree with the last post. If you have a server, one of the main concerns is security. Installing a GUI usually means that you are installing other programs that work with the GUI. The more programs that are installed, the more holes or potential entry points you create to your server.

> **techstop said:**
> Exactly. You want to minimise the potential for attackers to exploit vulnerabilities in your server. This means only installing the packages you need. A GUI is not necessary or recommended for a secure server.

So the most secure server is the one not running anything. 
It's also the most useless server. 

:)

---

### Post by koenn on 2009-05-02
> **pepeantonio1 said:**
> OK, 
What I have learn:
 - Apparently the best way to run Ubuntu applications is using freeNX on the Ubuntu computer and installing a NX client on the Windows PCs (Nomachine NXClient seems to be the perfect candidate)

**What is NOT clear to me is:**
-What version of Ubuntu should I use. Is it Edubuntu, Ubuntu and then is it Desktop or Server or the Alternate install with LTSP? **I'm  CONFUSED**!! **PLEASE HELP** with this as I do have little time for this project and I don't want to take the wrong route.

NX is a sophisticated way of X forwarding, so you don't need Edubuntu (it's an entirely different concept)
You can probably just start with the server version, install NX and any software it requires, and then install your applications. 
This will pull in large parts of the X system as well, as dependencies of your applications and/or of NX, but that's not a problem. After all, you *want* these apps installed and running on your server.

this might give you an idea of what you're trying to accomplish : [http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm) (the part about remote applications)

---

### Post by Carlos Pena on 2009-05-02
Hola PepeAntonio,

Lo que necesitas es instalar Apache y Samba. Ambos estan instalados si seleccionaste la opcion LAMP en la instalacion. Apache es el servidor para web applications y Samba es el servidor que simula Microsoft. En adicion a esto debes instalar MySQL que es servidor de base de datos MYSQL.

Saludos,

Carlos Pena
Santo Domingo,
Dominican Republic

---

### Post by koenn on 2009-05-02
> **Carlos Pena said:**
> Hola PepeAntonio,

Lo que necesitas es instalar Apache y Samba. Ambos estan instalados si seleccionaste la opcion LAMP en la instalacion. Apache es el servidor para web applications y Samba es el servidor que simula Microsoft. En adicion a esto debes instalar MySQL que es servidor de base de datos MYSQL.

Saludos,

Carlos Pena
Santo Domingo,
Dominican Republic

no no no no

Installing a web server, a file server and a database server is NOT going to help if you want to run remote applications. 

If you want tp run remote applications, you have to set up a server that provides remote applications.

---

### Post by pepeantonio1 on 2009-05-02
koenn,
Thank you very much for pointing me in the right direction. It is interesting that many people don't quite understand the concept of an Application Server which is what I want to have. Now a question:

When you say _"You can probably just start with the server version, install NX and any software it requires, and then install your applications." _you mean I can install all my applications on the server without the need to run them on the console, but having something like NX will allow me to run them from a remote machine, correct?
Thanks for your help!!
Cheers,

---

### Post by pepeantonio1 on 2009-05-02
Hola Carlos,
Hacer una installacion de Samba, Apache y MySQL es parte de una instalacion de un server LAMP, pero eso no es lo que yo quiero. Mi proposito principal es tener un servidor donde yo pueda installar varias applicaciones y correrlas en el server desde una estacion remota.

Piensa en cosas como OpenOffice, Firefox, GNUcash, Wireshark, etc que esten instaladas en el server y que yo pueda correr abriendo una sesion remota desde una PC con Windows o Linux porque no.

 Quizas despues que mis applicaciones esten installadas y funcionando alguna de ellas requiera alguno de esos componentes y entonces los instalare. Por ejemplo si alguna de mis applicaciones usa base de datos lo mas logico es que installe un server MySQL tambien o si quiero tener algun website y desarrollarlo puedo usar el Apache para hostearlo. 
Gracias por tus comentarios
Saludos

---

### Post by techstop on 2009-05-02
> **koenn said:**
> So the most secure server is the one not running anything. 
It's also the most useless server. 

:)

Don't be ridiculous.

You must have missed the part where I said;

> This means only installing the packages you need.

---

### Post by koenn on 2009-05-02
> **techstop said:**
> Don't be ridiculous. You must have missed the part where I said;

Quote:
This means only installing the packages you need. 


The OP wants to run applications of a server. Apps with GUIs. Evidently, that's just "installing the packages he needs". Is it not ridiculous then to tell him 
> **techstop said:**
> A GUI is not necessary or recommended for a secure server.

---

### Post by koenn on 2009-05-02
> **pepeantonio1 said:**
> koenn,
Thank you very much for pointing me in the right direction. It is interesting that many people don't quite understand the concept of an Application Server which is what I want to have.

that's partially because the term application server is usually used for a server that serves **web** apllications. What you're doing is called server-based computing, "application delivery over network",  or "terminal services" in MS speak.

> **pepeantonio1 said:**
> 
When you say _"You can probably just start with the server version, install NX and any software it requires, and then install your applications." _you mean I can install all my applications on the server without the need to run them on the console, but having something like NX will allow me to run them from a remote machine, correct?

yes, that's correct. 
Not only do you not need to run them on the console, most likely you won't be able to because they wouldn't have a (graphical) display available. You'll start them from a remote machine, they will run on the server, but their display will be visible on the remote machine.

---

### Post by techstop on 2009-05-02
> **koenn said:**
> The OP wants to run applications of a server. Apps with GUIs. Evidently, that's just "installing the packages he needs". Is it not ridiculous then to tell him

No, not at all, because my comment was related to the more general assertion that;

> **HermanAB said:**
> Howdy, 

There are many old reasons why one should not run a GUI on a server.  Most of those reasons are now obsolete, because servers are fast and RAM is cheap.

If your server has a screen and keyboard attached, then by all means, install a GUI, but consider switching to runlevel 3.  When you need to do something GUIsh, run startx and when you are done, exit it.  That way, you have the best of both worlds.

So of course, if you need a server to have a GUI, then you need it to have a GUI. If, on the other hand, you think you should install one just because "servers are fast and RAM is cheap", then that's another thing entirely.

---

### Post by pepeantonio1 on 2009-05-05
> **koenn said:**
> that's partially because the term application server is usually used for a server that serves **web** apllications. What you're doing is called server-based computing, "application delivery over network",  or "terminal services" in MS speak.


yes, that's correct. 
Not only do you not need to run them on the console, most likely you won't be able to because they wouldn't have a (graphical) display available. You'll start them from a remote machine, they will run on the server, but their display will be visible on the remote machine.

Thanks koenn! Your help is very much appreciated. I have no further questions regarding this particular issue. I hope I can get your help some other time if I have other questions!
Cheers,
Pepe

---

### Post by gtr32 on 2009-05-05
> **pepeantonio1 said:**
> 
I don't really specifics instructions, just a little bit of guidance. My goal is to have an application server where more than 2 Windows users can log in and run those applications.

SSH + XMing

[http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

---

### Post by koenn on 2009-05-05
> **pepeantonio1 said:**
> Thanks koenn! Your help is very much appreciated. I have no further questions regarding this particular issue. I hope I can get your help some other time if I have other questions!
Cheers,
Pepe
No problem, 
have fun.

---

### Post by pepeantonio1 on 2009-05-05
> **gtr32 said:**
> SSH + XMing

[http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

Hi gtr32,
Thanks for that link! Great post.
Cheers,

---

