---
title: "GUI for basic management of Ubuntu Server"
date: 2015-12-29
forum: Server Platforms
---

### Post by NotQuiteSU on 2015-12-29
I just installed Ubuntu Server 14.04.3 LTS. I've gone through a guide or 2 on making Samba shares, but I was hoping for a good web interface or GUI for SMB share management. Most applications I'm going to install will have a web interface, but it would be nice to have a GUI for some small stuff like share/drive management.

---

### Post by SeijiSensei on 2015-12-29
[https://www.samba.org/samba/GUI/](https://www.samba.org/samba/GUI/)

---

### Post by NotQuiteSU on 2015-12-29
any suggestions to a specific tool?

---

### Post by MAFoElffen on 2015-12-29
@NotQuiteSU: SeijiSensei gave you a link to one. I have to admit that I haven't tried that one yet. (And he just got my interest up enough to play with that to eval that...)

Me? I just edit my shares manually via the text smb.conf configuration file... but I tudor college students Linux. I introduce them to server admin via using  Webmin, which has a module for smb shares. For small businesses, where they want one of their own onsite to do their own admin, I consulted them in using Zyntal Server, which uses Samba smb shares. So that would be 2 additional GUI tools to help you if you are not text-based friendly. 

But who I tudor, even though I show them Webmin, I teach them what each piece of everything does and how to admin on the fly, manually. I'm always a fan of saving labor, but I know that if you understand what has to happen in the background,
and how the pieces work together, then if something does not work, then you might have a chance to understand what might be wrong. (or what to look through to find what is wrong.)

Learn the sections of the smb.conf file and what they do ... There's really not much to it's config once you figure out how it works ... Only a few sections actually get changed in a basic install.

---

### Post by bab1 on 2015-12-30
> **MAFoElffen said:**
> @NotQuiteSU: SeijiSensei gave you a link to one. I have to admit that I haven't tried that one yet. (And he just got my interest up enough to play with that to eval that...)

The page @ SeijiSensei linked to shows multiple GUI apps that serve different functions.  The OP was asking for advice on which of those to use.

I also just edit the smb.conf file if I'm working on a standalone file server.  So also my advice is to use that method.  It is faster, easier and can be done remotely (via ssh) once you learn all the parameters.  The smb.conf parameters are available using the man pages (man smb.conf). 

All you need to do is install Samba and add a share definition at the bottom of the smb.conf file.  The bare minimum share definition is```
[ShareName]
        comment = <describe your share>
        path = <data/lives/here>

```
Substitute your names and path for my <names and path>

---

### Post by NotQuiteSU on 2015-12-30
@bab1 AND @MAFoElffen

Thank you for your replies. I've decided to continue by editing the smb.conf file. If I want to learn from the ground up and truly understand how it is all working, this is the best way.  I'm not in a rush since I have a working host for my needs. So I can be patient and take my time.

---

