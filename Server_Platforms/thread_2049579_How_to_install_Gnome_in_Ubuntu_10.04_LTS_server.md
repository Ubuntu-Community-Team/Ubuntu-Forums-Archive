---
title: "How to install Gnome in Ubuntu 10.04 LTS server"
date: 2012-08-28
forum: Server Platforms
---

### Post by aman pal on 2012-08-28
Hello everyone!

I'm new to the Linux Ubuntu server configuration and after researching for a way of installing a visual package like Gnome, Kde i got into a deadend. I've tried to use and install some of this packages but somehow something is not going right.

i've used the followings commands and install the different three packages but after rebooting the server, i still get the command line visual like "MS-DODS"

sudo apt-get ubuntu-desktop

sudo apt-get xubuntu-desktop

sudo apt-get kubuntu-desktop


Can anyone help me by giving me some kind of guide or an ideia of what could be wrong... Thank you

Best regards

---

### Post by wojox on 2012-08-28
```
startx
```
Do anything? Did you install the Desktop and reboot after each one?

---

### Post by aman pal on 2012-08-28
yes by using startx it fails to initiate... Basically the errors are "screen found, but none have a usable configuration" and below "Fatal Server Error, no screens found", below "xinit:no such file or...:unable to connect to X server" and "xinit:No such process (errno 3) : Server error... I've rebooted the server after each try/installation

---

### Post by wojox on 2012-08-28
Looks like your video driver. Nvidia?
I would download a fresh Ubuntu 10.04 Desktop iso and install that if you want a GUI.

---

### Post by aman pal on 2012-08-28
The ubuntu server is installed by the provider! Ubuntu 10.04 LTS server! The rest is up to the client... so it's not a choice. Could it be the screen configuration and how to configure it? Maybe formating and instaling Ubuntu server again? Kind out of ideas here...

---

### Post by cariboo on 2012-08-29
> **aman pal said:**
> The ubuntu server is installed by the provider! Ubuntu 10.04 LTS server! The rest is up to the client... so it's not a choice. Could it be the screen configuration and how to configure it? Maybe formating and instaling Ubuntu server again? Kind out of ideas here...

If you are going to reformat, why not just install the Ubuntu desktop?

---

### Post by aman pal on 2012-08-29
Maybe i din't set myseld clear at the first time so again. Linux is installed by the server provider... There is no ubuntu desktop to install. They don't offer that choice! They install ubuntu 10.04 LTS server and do not install visual interfaces either have them available. It's up to the client to do it...

---

### Post by wojox on 2012-08-30
> **aman pal said:**
> The ubuntu server is installed by the provider!

How do you connect to your remote server?

---

### Post by aman pal on 2012-08-31
Through ssh.

---

### Post by kennethconn on 2012-08-31
Do you really need a GUI?
What is it you are trying to do once you have the GUI installed?
 
Command line is pretty straight forward when you look into it, and most of the guides for the servers are command line instructions. It might seem to you from the responses that people are not helping you out right now, but in fact, are. It's been a while since I installed a desktop, but I think you may need to edit files before startx works for you (so you are at command line anyway).

---

### Post by cariboo on 2012-09-01
> **aman pal said:**
> Hello everyone!

I'm new to the Linux Ubuntu server configuration and after researching for a way of installing a visual package like Gnome, Kde i got into a deadend. I've tried to use and install some of this packages but somehow something is not going right.

i've used the followings commands and install the different three packages but after rebooting the server, i still get the command line visual like "MS-DODS"

sudo apt-get ubuntu-desktop

sudo apt-get xubuntu-desktop

sudo apt-get kubuntu-desktop


Can anyone help me by giving me some kind of guide or an ideia of what could be wrong... Thank you

Best regards

Your commands are wrong, it should be:

```
sudo apt-get **install** ubuntu-desktop

sudo apt-get **install** xubuntu-desktop

sudo apt-get **install** kubuntu-desktop
```

If you've actually installed the desktop meta-package, have you tried x-forwarding eg:

```
ssh -X user@server
```

note the X is upper case. Then type the name of the program you want to use for example, the ubuntu desktop file manager is nautilus, so once you have connected to the server, type:

```
nautilus
```

---

### Post by aman pal on 2012-09-01
Sorry guys, but that command is invalid on my server! ssh -X user@server

The purpose on installing a visual interface is because im installing some BF2 servers (non-dedicated) and some moddings are needed. It would be much faster using a desktop visual interface to do that (/copy/replace/edit files)... I think im going to research more stuff... Anyways i still can do it in command line, just have to serach for the right command lines. Thanks again. Best regards

---

### Post by arrrghhh on 2012-09-02
> **aman pal said:**
> Sorry guys, but that command is invalid on my server! ssh -X user@server

The purpose on installing a visual interface is because im installing some BF2 servers (non-dedicated) and some moddings are needed. It would be much faster using a desktop visual interface to do that (/copy/replace/edit files)... I think im going to research more stuff... Anyways i still can do it in command line, just have to serach for the right command lines. Thanks again. Best regards

The server will run better, and honestly be less vulnerable if you leave the desktop environment off of it.

However, if you're perplexed on the ssh -X command, it might be because that command is run on the ***client*** machine.  The one you are using to connect to your Ubuntu Server that is from your provider?

So if you are using PuTTY on Windows, you will need XMMing, FYI.  Then you will just need to configure the PuTTY client to forward X sessions on to your localhost, and blam you should have a local X server to run XWindows on.  

However, I would still recommend you stick with cli-only!!  Much easier to manage, and less things to break ;).

---

### Post by aman pal on 2012-09-03
Yeap... guess i'll have to get used to the shell. At least i'm learning some new stuff. I only have one question... I've uploaded one zip file from a website using wget... but besides the .zip file came a 9238012384102.html file wich i can't delete. Any ideas of what that might be and how to delete it? Thanks

---

### Post by arrrghhh on 2012-09-04
> **aman pal said:**
> Yeap... guess i'll have to get used to the shell. At least i'm learning some new stuff. I only have one question... I've uploaded one zip file from a website using wget... but besides the .zip file came a 9238012384102.html file wich i can't delete. Any ideas of what that might be and how to delete it? Thanks

sudo rm -f never fails (which can make it dangerous!).  Are you doing the rm command with sudo or not?  If you're doing it with just your user, your user might not have the necessary rights to delete the file.

Check file permissions with ls -l

---

### Post by wojox on 2012-09-04
> **aman pal said:**
> Sorry guys, but that command is invalid on my server! ssh -X user@server

You did replace user with your username and server with the address correct?

---

### Post by kennethconn on 2012-09-04
> **wojox said:**
> You did replace user with your username and server with the address correct?
 
Someone has served their time in support!!

---

### Post by aman pal on 2012-09-05
Apparently shutting down the connection and connect again solved the problem for removing the file. I'm also concerned about the fact that i'm not capable of downloading zip files to the server and unzipping them... a friend of mine tried with the same link and the after that i was able to unzip it... Everytime i download a zip file and test it (unzip -t) it says its not a .zip file.

About the ssh -X user@server nautilus it says cannot open display

i'm also trying to install mono-1.1.12.1 on the server so that i can run bf2ccd, wich is an admin tool for the game servers i installed, everything is allright but when i execute the following command

mono bf2ccd.exe

it runs another error that says that the assembly referenced from /.../bf2ccd.exe could not be loaded.

those are kind of specific questions. Sorry about that! Anyways thanks for all the help.
Best regards

---

### Post by arrrghhh on 2012-09-05
> **aman pal said:**
> Apparently shutting down the connection and connect again solved the problem for removing the file. I'm also concerned about the fact that i'm not capable of downloading zip files to the server and unzipping them... a friend of mine tried with the same link and the after that i was able to unzip it... Everytime i download a zip file and test it (unzip -t) it says its not a .zip file.

About the ssh -X user@server nautilus it says cannot open display

i'm also trying to install mono-1.1.12.1 on the server so that i can run bf2ccd, wich is an admin tool for the game servers i installed, everything is allright but when i execute the following command

mono bf2ccd.exe

it runs another error that says that the assembly referenced from /.../bf2ccd.exe could not be loaded.

those are kind of specific questions. Sorry about that! Anyways thanks for all the help.
Best regards

You should probably ask the BF2 question in another forum - it doesn't really have much to do with Ubuntu Server and you'll probably get better help elsewhere on that.  Plus, you're kind of thread-jacking your own thread.

Also, unzip -t?  What is the -t switch for?  What's the exact unzip command line you're using?  ```
unzip file.zip
```Works fine for me!

For nautilus, again - you have to have a local XWindows server running.  So if the box you're sshing **FROM** doesn't have XWindows (IE isn't running Linux) then you'll have to run something for XWindows.  On WinXP/7 I use XMMing.

---

### Post by aman pal on 2012-09-06
unzip -t file is to test if the file is good... Try on one of yours... If its not good you will not be able to unzip it. My error is that its not a .zip file... But the problem must be in wget file. For somehow every file i upload is corrupted.

---

### Post by directhex on 2012-09-06
> **aman pal said:**
> it runs another error that says that the assembly referenced from /.../bf2ccd.exe could not be loaded.

Without revealing the specific assembly which is missing, nobody can tell you what to install. But general case, mono-complete will probably pull it in.

---

### Post by aman pal on 2012-09-06
The assembly is the path to that file bf2ccd.exe, more specificly /root/Download/servers/oman/bf2ccd.exe...

Mono-complete? Problem is that there is no mono 1.1.12.1 for ubuntu. only for suse, redhat and fedora... Besides on the admin tool install tutorial says that further versions of 1.1.12.1 will no work. Can you give me a link to mono-complete for ubuntu 10.04?

---

### Post by directhex on 2012-09-07
> **aman pal said:**
> The assembly is the path to that file bf2ccd.exe, more specificly /root/Download/servers/oman/bf2ccd.exe...

That's not the error. An assembly reference error looks like this:

```
The following assembly referenced from /home/foo/bar.exe could not be loaded:
      Assembly:   Something    (assemblyref_index=4)
      Version:    0.1.0.0
      Public Key: 407dd0808d44fbdc
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/foo).
```

In this case the missing file is Something.dll, which can be found with "apt-file search Something.dll", which will report which package to install.

> Mono-complete? Problem is that there is no mono 1.1.12.1 for ubuntu.

I don't think you realise just how old that version is. (22-Dec-2005)

> only for suse, redhat and fedora... Besides on the admin tool install tutorial says that further versions of 1.1.12.1 will no work.

I would hope that they're mistaken. The most recent version of Ubuntu with Mono 1.1.12.1 or older is Breezy (5.10) which shipped with 1.1.8.3-1ubuntu2. This predates my involvement in Ubuntu or Mono.

> Can you give me a link to mono-complete for ubuntu 10.04?

[mono-complete](apt:mono-complete) - but on 10.04 this gives you a post-2.4.3 SVN snapshot of Mono.

---

