---
title: "Ubuntu server with edubuntu workstations"
date: 2006-01-01
forum: Server Platforms
---

### Post by ttaulman on 2006-01-01
I'm in the process of setting up a network in a school. The server is Ubuntu and the workstations are going to be edubuntu. I currently have Ubuntu set up and running apache, samba, nfs, squid, bind9 and several other things. The Edubuntu workstations are able to surf through the proxy and print on the network. Now here are the questions I need help with. I want to set it up so the workstations authenticate to the server and get their own user space. Do I need to do something on Ubuntu for this? And on the Edubuntu workstations, how do I change the login so that I can attach to the Ubuntu domain? Thanks for any help! It's been fun getting this much to work!:smile:

---

### Post by bluefrog on 2006-01-02
you could setup samba-ldap for central authentication for example.
or use edubuntu as server.

james

---

### Post by ttaulman on 2006-01-03
I'll give it a try. I assume LDAP is a better route than NIS. Do you know exactly what I change to make edubuntu log into a server rather than just logging into itself locally?

---

### Post by bluefrog on 2006-01-04
depends on what you want to do.

if u use thin clients, setup an edubuntu server and you're done.

if u use thick clients, u have to setup a samba-ldap server (for example) and configure the thick clients to authenticate against it.

james

---

### Post by ttaulman on 2006-01-04
This all sounds like what I was thinking. I have several new computers for the lab and want them to be thick clients. The old computers, I want them to be thin. I tested that part last night and was able to login as a thin client. The part I am still unsure of is what to change on the Edubuntu machines to make them authenticate. I have samba and ldap running and I think I have my configs set up corecttly for them. Do I just map to a users home on the server? Or are there other things that need to run on the client?

---

### Post by ttaulman on 2006-01-06
OK, this sounds dumb to me, but I'm missing something. How do I make the other Edubuntu machines logon to the server, authenticate and then get their mapped drive (/home directory on the server). They don't need to be a thin client, I got that to work and it is cool, but I don't need the new computers doing that since they have plenty of horsepower on their own. I just want all the users to save on the server so it can all be backed up. This shouldn't be so hard. I know samba does it for Windows machines and does it well. I guess I just don't know what to change so that I logon on similar to Windows (before GDM?) so that I get /home directories. Help, any ideas?

---

### Post by Luuraja on 2006-01-06
[QUOTE=ttaulman]...How do I make the other Edubuntu machines logon to the server, authenticate and then get their mapped drive (/home directory on the server). They don't need to be a thin client...[/QUOTE]

I need to solve this issue too!
Thin clients are working well, just setup the XDMCP connection with server, everything you need works out-of-box. 
But problem rises when I try to connect with server from standalone Edubuntu workstation. FTP access works well, but I need to bring my server-side desktop to workstations screen.
Terminal Server Client has XDMCP disabled and VNC is boringly slow.

Any ideas. Has I missed something important?

---

### Post by ttaulman on 2006-01-10
I don't know if this will help you or not. I found this looking for an easy way to do exactly what I wanted. Matt has written a wonderful looking script to put samba and ldap on the server. ([http://majen.net/smbldap/]("http://majen.net/smbldap/")) I didn't get it working on the first try and emailed him for suggestions. I'm in the process of starting on this again and will keep you posted. If I get this working, I'm sure I can use it again. Best of all, it will all be easy to use because it is Ubuntu/Edubuntu!

---

