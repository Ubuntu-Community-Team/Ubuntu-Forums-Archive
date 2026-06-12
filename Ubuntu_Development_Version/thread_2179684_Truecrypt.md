---
title: "Truecrypt"
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by nah40 on 2013-10-09
How to install truecrypt in Saucy.

---

### Post by grahammechanical on 2013-10-09
Why do you think that it would be different for Saucy then for Raring? Unless of course the developers of truecrypt have not yet packaged their software for saucy. The Ubuntu 13.10 Software Centre has in something called tcplay. It is described as

> as a free (BSD licensed), pretty much fully featured (including multiple keyfiles, cipher cascades, etc) and stable TrueCrypt implementation

There you are. It is the same in Saucy as for Raring.

---

### Post by nah40 on 2013-10-09
It is not the same.

---

### Post by cariboo on 2013-10-09
Are you downloading the application from [here]("http://www.truecrypt.org/downloads")? If so, use file-roller to extract it, then run the setup. In my case I downloaded the 64 bit version:

```
sudo ./truecrypt-7.1a-setup-x64
```

a window will pop up and walk you through the setup process. Once you have it installed, open a terminal and type:

```
truecrypt
```

---

### Post by rrnbtter on 2013-10-10
Greetings,
Truecrypt is installed from a bash script. I copy the setup script to my bin directory and run it from the command prompt. Works perfect for me. I also create a .desktop file and icon to put on my launcher. Truecrypt is one of my must have programs.

---

### Post by nah40 on 2013-10-10
> **cariboo907 said:**
> Are you downloading the application from [here]("http://www.truecrypt.org/downloads")? If so, use file-roller to extract it, then run the setup. In my case I downloaded the 64 bit version:

```
sudo ./truecrypt-7.1a-setup-x64
```

a window will pop up and walk you through the setup process. Once you have it installed, open a terminal and type:

```
truecrypt
```

Installed file-roller, but cannot figure out how to use it to extract Truecrypt.

---

### Post by JMB74 on 2013-10-10
Just use tar to extract.

**tar xf truecrypt-7.1a-setup-x64.tar.gz**

---

### Post by rrnbtter on 2013-10-10
Greetings,
Everyone has their preferences here but Archive Manager is preinstall with Saucy. I don't see why someone would have a problem right clicking on a file and choosing to extract the file. Especially when they joined the forum in 2006. Am I missing something?

---

### Post by nah40 on 2013-10-10
> **rrnbtter said:**
> Greetings,
Everyone has their preferences here but Archive Manager is preinstall with Saucy. I don't see why someone would have a problem right clicking on a file and choosing to extract the file. Especially when they joined the forum in 2006. Am I missing something?

I can extract the file with Archive Manager, but the resulting setup file has no application opening option except gedit.
I have never had a problem installing Truecrypt in other Ubuntu versions.

---

### Post by JMB74 on 2013-10-10
You run the setup script as cariboo has already told you.

> **cariboo907 said:**
> Are you downloading the application from [here]("http://www.truecrypt.org/downloads")? If so, use file-roller to extract it, then run the setup. In my case I downloaded the 64 bit version:

```
[COLOR=#ff0000]**sudo ./truecrypt-7.1a-setup-x64**[/COLOR]
```

a window will pop up and walk you through the setup process. Once you have it installed, open a terminal and type:

```
truecrypt
```

---

### Post by nah40 on 2013-10-10
Right clicking the setup file gives the option of opening with gedit or searching online for an application which comes up with emacs.

---

### Post by JMB74 on 2013-10-10
You don't right click anything. :confused:

Just run

[COLOR=#ff0000]**sudo ./truecrypt-7.1a-setup-x64**[/COLOR]

---

### Post by nah40 on 2013-10-10
Tried that first.
Result is command not found.
That works for prior Ubuntu versions, but not currently on my installation of 13.10

---

### Post by JMB74 on 2013-10-10
sudo? Command not found? That is rather worrying.

Or are you mistyping the script filename?

The install file is an executable script. You need to run it via the command line with root/sudo privileges.

---

### Post by nah40 on 2013-10-10
No checked multiple times.

---

### Post by JMB74 on 2013-10-10
You are doing something strangely wrong, as it works just fine here as below.

[IMG]http://i.imgur.com/vCEV1RX.png[/IMG]

---

### Post by rrnbtter on 2013-10-10
Greetings,
This is what works for me. 
1. Rename the truecrypt-7.1a script file to "truecryptsetup". No extension is needed. Under the file properties check "execute as program". Also make sure that you have permission to execute the file. Then copy/move the file to /bin. From the prompt type "truecryptsetup", you should get the display shown in post #16. 
[COLOR=#ff0000][/COLOR]

---

### Post by nah40 on 2013-10-10
JMB74

I have been using Ubuntu and Truecrytp for 6 years and have not had a problem like this one.
that may work for you, but not for me.

---

### Post by nah40 on 2013-10-10
> **rrnbtter said:**
> Greetings,
This is what works for me. 
1. Rename the truecrypt-7.1a script file to "truecryptsetup". No extension is needed. Under the file properties check "execute as program". Also make sure that you have permission to execute the file. Then copy/move the file to /bin. From the prompt type "truecryptsetup", you should get the display shown in post #16. 
[COLOR=#ff0000][/COLOR]

That worked.
Thank you

---

### Post by JMB74 on 2013-10-10
Glad you got it working.

A tad odd that you had to do it that way, as running the install script directly should work.

---

### Post by rrnbtter on 2013-10-10
Greetings,

> **JMB74 said:**
> Glad you got it working.
A tad odd that you had to do it that way, as running the install script directly should work.

Seems to me that permissions on the file were wrong or a problem with path. 

What I do with scripts to make it easy is to create a "bin" dir in my home directory and copy this line into my .bashrc file. "if [ -d "$HOME/bin" ] ; then
  PATH="$PATH:$HOME/bin"
fi"

I put all of my scripts in "home/bin" and they execute with no problem and they don't get mixed in with the system scripts. In addition I add them to my backup so I always have a copy. 

At any rate its a pleasure to finally know enough to be able to help someone.

---

### Post by JMB74 on 2013-10-10
Possibly execute permissions? The tarball was extracting for me with the script ending up executable without needing to set it so. Possible that a quirk of another system was not setting that for some reason?

Must be I suppose, as running sudo ./script should always work. You shouldn't need to mess about renaming and moving the file to be in your path.

In the end though it is whatever works for you......

---

