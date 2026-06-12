---
title: "post installation issues on ubuntu server 10.10"
date: 2011-09-21
forum: Server Platforms
---

### Post by Miqueridosims on 2011-09-21
Hello my friends:
  I am a newbie in linux and I need your help.
  I have an old machine that was sleeping on my storeroom and I decided to put it to work.
  So I chose to install ubuntu server 10.10, that because my pc did not like 10.04LTS what I wanted.
   
  After 2 installations I got it up and running, now I can read and write on the windows computers; however I still have some issues. Let me explain.
   
  My computer has 128 in RAM, I can get more ram of course but I read that the server will run with the 128 so as I said before I wanted to try.
   
  I am using the following software:
  Ubuntu server 10.10
  Putty
  TightVNC viewer
  Webmin.
   
  Putty worked just fine pretty straight forward.
  TightVNC, I am able to login and see the virtual desktop, however two things are happening when I a use VNC: when I key the &#8220;d&#8221; key the terminal goes away and cannot see it any more, and the other thing is if I install either gparted or synaptic asks me for a password which supposed to be, however it doesn&#8217;t accept the password that I set during the installation and I cannot use it.
  Other thing is if I create a folder through either putty or terminal, then I cannot change the permissions in VNC.
   
  Webmin: using webmin I am able to create users and shares, however doing the shares doesn&#8217;t work. Any share that I create through webming works partially. Let me explain:
  I can see the shared folder however the password that I set in webmin is not take it in windows, so I need to set the ssh sever to accept empty passwords.
   
  The other thing is that I have to create the shared folder through VNC only, otherwise just does not work if I create the folder either in putty or in webmin.
What I mean by that is what I said before, I am not allow to change permissions and when I map the driver in Windows it doesn't allow me to write on it. I get a message which it says "access denied" or something like that.
   
  Any recommendation, suggestion or advice is welcome and really appreciated.
   
  Thank you all in advance.

---

### Post by Miqueridosims on 2011-12-26
In order to understand better the file sharing through Samba I decided to read a little about the samba configuration file smb.conf. I did read the info from Samba website and it was good, I did a practice in another computer how to configure this file and I got it work.
   
  This is what I did to correct this situation (everything was done in terminal)
   
  1.- I created new users in the server and in Samba to start fresh with these users.
   
  2.- I change the SECURITY = SHARE, before I had set the security = user. I still don’t know what the difference is but did work.
   
  3.- After I got this work I updated my original share and did work as well.
   
  So if you are not expert in Linux / Ubuntu I recommend the following:
   
  -         Learn about linux file system structure.
  -         How to set users through terminal
  -         How to use nano (this is a text editor which helps to modify configuration files).
  -         Learn about Samba configuration file (here is the link )
  -         [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
   
   
  Hope this helps to anyone who wants to user a file sharing server.

---

