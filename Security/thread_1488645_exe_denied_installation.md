---
title: "exe denied installation"
date: 2010-05-20
forum: Security
---

### Post by pdlethbridge on 2010-05-20
I did a fresh install of 10.04 to try it again. Some things I got running successfully like my printer and scanner but I was unable to get the tv capture card working. While trying some other software, I ran into a very bad problem. I was unable to install 2 exe. files I used in windows and in 9.04 in wine. I have never had a problem with either of these programs since I started using Ubuntu in version 6.04. The error message was that it wasn't a ubuntu approved software and it wouldn't allow me to install this because of the fear of virus's, trojans etc.
 One file was RTS10setup.exe from [http://www.atlasrr.com/righttrack.htm](http://www.atlasrr.com/righttrack.htm) and the other was the watchtower on CD. I was even logged as the admin, so what gives?

---

### Post by cdenley on 2010-05-20
You mean this message?
> 
The file 'filename.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the [executable bit]("https://wiki.ubuntu.com/Security/ExecutableBit").


After reading that and browsing the link which you were given:
[https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)
what questions do you still have?

---

### Post by pdlethbridge on 2010-05-20
How do I get them to install?

---

### Post by cdenley on 2010-05-20
> **pdlethbridge said:**
> How do I get them to install?

If you understand the risks involved in running executables from arbitrary, unverified sources, you mark it as executable.

You can do this with nautilus:
Right-click file, choose "Properties". Select the "Permissions" tab. Check the "Execute" checkbox.

Or you can do it from the terminal:
```

chmod +x myfile.exe

```

By doing this, you essentially grant that executable full access to your account. Even if you trust your user account to Atlas Model Railroad Co, the company distributing that executable, you also trust that their server hasn't been compromised or spoofed.

---

### Post by pdlethbridge on 2010-05-20
Almost sounds like paranoia!

---

### Post by cdenley on 2010-05-20
> **pdlethbridge said:**
> Almost sounds like paranoia!

No, just common sense security. Linux isn't more secure simply because it is less common. Windows gets infected because people download and run just about anything. With ubuntu, most people can just stick to the trusted software repositories.

---

### Post by pdlethbridge on 2010-05-20
Sorry, it's paranoia. Once in a while people use common sense and download safe files. I can understand that most users don't know a safe file from a unsafe one. But for those of us who would like to use a safe program, don't tie our hands with this paranoia.

---

### Post by cdenley on 2010-05-20
> **pdlethbridge said:**
> Sorry, it's paranoia. Once in a while people use common sense and download safe files. I can understand that most users don't know a safe file from a unsafe one. But for those of us who would like to use a safe program, don't tie our hands with this paranoia.

Your hands aren't tied, and it isn't paranoia. They are just finally applying existing filesystem restrictions (which have been in place for decades and has worked quite well) to windows executables. You can't and never could execute linux executables without the executable bit. This is even more important for windows executables. This has always been how linux and unix-based operating systems have worked. The executable bit is there for a very good reason.

---

### Post by pdlethbridge on 2010-05-20
they should still make it easier to change without all the hoops to jump through. In 9.04, a warning comes up about the potential dangers of the software being installed, Hey, they could use bold type and use red for the color.

---

### Post by teh_drizzle on 2010-05-20
> **pdlethbridge said:**
> Sorry, it's paranoia. Once in a while people use common sense and download safe files.

Paranoia is also setting the background to black and popping up a small window saying "OMG you're trying to use a computer, make sure you know what you're doing!" every time you want to install / uninstall / change the background / open the windows update / etc (UAC). Every operating system has it's quirks. And although there is no setting (as far as I know) to automatically set the execution bit for downloaded programs, it does make things easier. You can delegate who on your computer can run the program by setting the execution bit only for yourself or for the group your in. And as long as you're transferring the file within supported file systems the bit will stay on. (It's not something you have to explicitly state every time you want to 'use' the file, just a one time deal) (unless you change your mind about who can run the program). 

The hoop is a one line command, that's a pretty easy hoop IMO. 

Cheers!

---

### Post by cdenley on 2010-05-20
If you want to be able to run the executable from the "not marked as executable" warning:
```

sed -e 's/^\(.*\/usr\/bin\/zenity \)--error \(.*<\/a>\.\).*$/\1--question \2 Would you like to execute it?" \&\& exec "$@" "$exe"/' /usr/bin/cautious-launcher|sudo tee /usr/local/bin/cautious-launcher
sudo chmod a+rx /usr/local/bin/cautious-launcher

```

If you want to revert back to the original launcher:
```

sudo rm /usr/local/bin/cautious-launcher

```

---

### Post by OpSecShellshock on 2010-05-20
There's nothing in the OS that's stopping a system owner from making the necessary changes that will allow these executables to run. Hardly seems accurate to think of it as a restriction or even as an obstacle. IMO it's better to disable the function by default and allow system owners to change it if they need to than to go at it the other way around.

---

### Post by pdlethbridge on 2010-05-20
I did what was suggested and did get the programs installed. It was only a tiny hoop, just a lot of hoopla on my part. My bad.:-#

---

