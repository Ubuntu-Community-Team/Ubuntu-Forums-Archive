---
title: "Small Business Servers"
date: 2010-01-25
forum: Server Platforms
---

### Post by Matsuri on 2010-01-25
This may be a stupid question or a very broad question but I'm having trouble finding good documentation or a place to start. I'm looking to create a small business server, that allows file sharing, storage. 3-4 machines will need to be able to login the server, where all the shared and private data for that user will be stored. Something close to what businesses get out of Windows Server... So any user can sit down at any of the 4 computers, login, and have access to all of their data and files.

I'm new to Linux Networking, so forgive if this is a stupid / broad / long question to answer. Just need a place to start learning.

---

### Post by munky99999 on 2010-01-25
[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

or the link in my signature.

---

### Post by Lars Noodén on 2010-01-25
> **munky99999 said:**
> [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html) or the link in my signature.

Specifically the [Section on Samba](https://help.ubuntu.com/9.10/serverguide/C/windows-networking-introduction.html).

---

### Post by junapp on 2010-01-25
might be worth looking into:
[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

haven't tried it yet.

article at:
[http://www.linux-mag.com/cache/7662/1.html](http://www.linux-mag.com/cache/7662/1.html)

---

### Post by Matsuri on 2010-01-25
Awesome, thanks. I'll start reading more into these when I get home from work. Thanks for the input!

Matsuri

---

### Post by Matsuri on 2010-01-25
More looking for documentation on how to setup Ubuntu Server to do things similar to for example, a University, does. Students can sit down at any computer, login and access all of their files as if they were sitting at their home computer. I don't know if any of this makes sense, ... lol.

---

### Post by nyu2007 on 2010-01-25
Hi Matsuri,

I repared to setup an new system for small business (PDC, SAMBA,....) for about 50 users. Like to research with you.

---

### Post by munky99999 on 2010-01-26
> I repared to setup an new system for small business (PDC, SAMBA,....) for about 50 users. Like to research with you. 
[http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

150megs for vm or iso. Not much setting up needed.

---

### Post by Matsuri on 2010-01-26
> **munky99999 said:**
> [http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

150megs for vm or iso. Not much setting up needed.

I'm not interested in a magical tool that does it all. I want to actually learn how to do it. I'm by no means a hack when it comes to command line, I don't mind not having a cute graphical interface. The pretty white cursor is all I need.

---

### Post by Lars Noodén on 2010-01-26
> **Matsuri said:**
> More looking for documentation on how to setup Ubuntu Server to do things similar to for example, a University, does. ...

Can you give us a ballpark figure on the number of users?  Optimal methods for tens of users often are not optimal for thousands, and vice versa.

> **Matsuri said:**
> ... I want to actually learn how to do it....

Kerberos will figure into that, plain or mixed with Samba.

If you are in the States, then there is a [2010 AFS and Kerberos Best Practices Workshop](http://workshop.openafs.org/afsbpw10/) May 24-28 at the University of Illinois, Urbana-Champaign (the home of Mosaic, Netscape and Apache).

---

### Post by Matsuri on 2010-01-26
Ok, read a lot of the Manual and have perhaps more specific questions. Setting up the server is overall pretty simple and straight forward. My question now refers to setting up the client computers. For kicks and giggles lets say 3 computers. How do I setup those computers so its more of a network login instead of a local computer login, so the user can access their files, data, etc.

Small business network, so say no more than 5-10 users.

---

### Post by HermanAB on 2010-01-26
You need LDAP.

I would use Mandriva Linux Small Business Server.  It does everything you need with nice GUI wizards just like Windows servers.

---

### Post by Lars Noodén on 2010-01-26
> **Matsuri said:**
> 
Small business network, so say no more than 5-10 users.

In that case, Samba is probably your best bet.  It will include OpenLDAP as @Herman AB recommends and use Kerberos for authentication.  It will also allow file sharing and print sharing. 

There are lots of guides for Samba in many contexts.  

One thing that might not be as widely known as it could be is that a web server can be given read-only access, via ACLs, to specific user directories and then the users can publish via WWW anything in the folder ~/www.  See [mod_userdir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html) if that is interesting.  

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

---

### Post by Matsuri on 2010-01-26
I thought SAMBA was primarily a Windows File Sharing server? All the machines in this network will be running Ubuntu or a similarly Debian based linux OS.

---

### Post by Lars Noodén on 2010-01-26
> **Matsuri said:**
> I thought SAMBA was primarily a Windows File Sharing server? All the machines in this network will be running Ubuntu or a similarly Debian based linux OS.

[Samba](http://news.samba.org/search/?q=allison) uses [smb](http://samba.anu.edu.au/cifs/docs/what-is-smb.html) which  is (IIRC) from IBM and is available for many systems.  cifs is the eee version of smb and despite the usual sounds about 'interop' and 'open', it takes [years of lawsuits to get the specs](http://www.groklaw.net/articlebasic.php?story=20070919214307459).  So CIFS is part of the reason it has the stigma of Windows, the other is that Windows is rather crippled in regard to files systems.  For example, just try to plug into Windows something as common as ext2 support.

But despite the stigma, Samba does work with Linux, BSD, Solaris and OSX clients.  It's well done and you could sell NAS appliances based on it.

If no machines on the network are running Windows, then your choices expand greatly.  NFS is one of the small scale traditional options.  

There are some that I haven't used yet, like [gfs](http://sources.redhat.com/cluster/gfs/).  And others which might not yet be available for linux, like ZFS, Hammer and Coda.

---

### Post by Matsuri on 2010-01-29
Ok, I will be trying this shortly. I'm currently either busy in the evening or dead tired. I'll give this a try this weekend and let you guys know hows it going and ask more questions, lol.

Matsuri

---

