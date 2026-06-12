---
title: "Creating secure encrypted archives - is RAR better than 7z?"
date: 2014-05-09
forum: Security
---

### Post by frogwarrior on 2014-05-09
I'm studying a non computer based science course in college and the lecturers aren't all that tech savvy and sometimes they do things in a very inefficient manner. I want to upload some data from the server in the lab to the web so that we can all access it, which would make life a whole lot easier for everyone. They get paranoid about uploading any research results to the web though, and I like to maintain some healthy paranoia myself so I wanna do this as securely as I possibly can. I'd appreciate any advice or suggestions. What I'm thinking is I compress all the data into a password protected .rar file, upload it to dropbox then we (the students) share the password with each other via SMS. I'll give instructions to everyone not to extract the whole directory of files from the archive, only to extract their own files (they're just NMR and IR spectra from undergrad research projects, not some top secret data, but like I said, I prefer to take the paranoid approach and do it as securely as possible) , that way if someones comp is infected with malware, at least the whole archive won't be mined by the malware. I know theres a risk of there being a keylogger/trojan on someones computer, but not much I can do about that but its not really that serious, I just don't wanna do this sloppily.  What is the best kind of archive for secure encryption? I read good things about .7z files, but I suspect .rar files are the most secure out there.  I wanna use AES encryption, do I need to explicitly specify AES encryption using the command line tool, or does the GUI use AES by default when you password protect a rar file? The way I usually password rar files (which is very seldom, I'm not a big fan of passworded rar files, pain in the ass IME) is with nautilus, I just right click on the folder I wanna zip:  [img]http://i.gyazo.com/88108de4033b634348ae8b17ce782a71.png[/img] but I don't know what kind of encryption it uses by default. Also there are a wide range of different archive types to choose from theres 7z, tar.7z, tar.gz etc. I don't know which are superior in terms of encryption security.

---

### Post by sudodus on 2014-05-09
Use Pretty Good Privacy encryption, if you want high security. The software ***gpg*** is available in linux and Windows. But it is more complicated than the encryption that comes with ***rar*** and other compressed archives, and I think rar is good enough in this case

Browse the internet and find links like this one

[http://www.stormfront.org/forum/t931854/](http://www.stormfront.org/forum/t931854/)

---

### Post by untrustytahr on 2014-05-09
I second gpg.  If you're doing multiple files in directories you'll use [gpg-zip]("https://www.gnupg.org/documentation/manuals/gnupg/gpg_002dzip.html").  If you want to use AES256 you can add --cipher-algo AES256 or alternatively put it in the gpg.conf file and it will be the default.
You have the option of symmetric/asymmetric but since some of your folks aren't technical, you're probably better off using symmetrical and not worry about key maintenence.

---

