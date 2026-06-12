---
title: "Language question"
date: 2012-03-22
forum: The Cafe
---

### Post by Diametric on 2012-03-22
Hello,

I am wondering how my interactions with servers would be different if I moved to a different country (Spanish speaking)?  Specifically - how are scripts handled?  If the language setting is changed on a server/pc are any scripts to be modified as well?  Or, must all code be in English?  How does that work?  

Does any one have any experience with this?

Thanks!

---

### Post by spynappels on 2012-03-22
Scripts are written in the language they are written in, if it looks like English, that is coincidental, the syntax is set. This means the commands in a Bash script written in Spain will be identical to those in a Bash script written in India.

The comments are a very different matter, they are normally written in whatever language the person writing/maintaining the script uses.

---

### Post by Diametric on 2012-03-22
So, an "echo" command is still command an echo command no matter where you are?

What about the directory structure?  Is everything still var etc bin?  Apps too - apache.

I guess what I'm driving at, is, if I find myself at a CLI in a Spanish speaking country (and I don't speak Spanish), other than the comments, will I be able to understand where I'm at and interact with the system as normal?

Thank you.

---

### Post by spynappels on 2012-03-22
All the commands and aliases (sp?) will be the same, as will the directory structure. 

You cannot be sure that commands which may use other text will be the same, for example MOTD will probably be in the language of the country you are in.

So I guess I'm trying to say that most stuff will be the same, but there may be some localised differences. That's why we have Google Translate!;)

---

### Post by odiseo77 on 2012-03-22
> **Diametric said:**
> I guess what I'm driving at, is, if I find myself at a CLI in a Spanish speaking country (and I don't speak Spanish), other than the comments, will I be able to understand where I'm at and interact with the system as normal?

Yes, it will be the same. The only thing that will be different, of course, is the GUI (for example, in the old GNOME 2, "Applications" is "Aplicaciones", "Places" is "Lugares", etc.), but as long as you're familiar with it you won't have any issues. What's underneath (file system structure, scripts, config files, etc.) is all the same, no matter if the system is in Spanish, English, or any other language (with the exception of the comments, as pointed by spynappels).

Cheers.

---

### Post by cgroza on 2012-03-22
About the comments, I remember reading source code that had comments both in English and German. It was probably the source of Dr.Python if I remember well, but I could be wrong.

---

### Post by Diametric on 2012-03-22
Cool.  Thanks for all your replies.

---

