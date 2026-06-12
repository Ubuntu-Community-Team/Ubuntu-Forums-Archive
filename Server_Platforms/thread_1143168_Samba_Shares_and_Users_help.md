---
title: "Samba Shares and Users help"
date: 2009-04-29
forum: Server Platforms
---

### Post by DoyleChris on 2009-04-29
I am using Webmin trying to setup Samba Shares on my network.  I have 2 users Myself and my Girlfriend.  What i am trying to do is setup the shares in Webmin and its not working.  I created the accounts in Webmin and converted them over from linux to the samba users and there set.  And im trying to create shares for folders on a drive in the maching Music, Movies, Programs on so forth.  i am trying to put them on one drive mounted at /Server but i having problems creating the directories though webmin but it gives the directory is created by root but im not sure what to do.  and if i cant change the permissions of the directories though webmin i haft to go into the server itself to set the permissions up.

---

### Post by Carlos Pena on 2009-04-30
How the computers will be conneted to server? LAN or via internet.

---

### Post by DoyleChris on 2009-04-30
My computer is connected to a LAN which is connected to a Monowall firewall, and the server is on a LAN connected also to the monowall firewall but on different cards.  I can see the share and everything its just i haft to change the permissions of the share in linux so people can use, and samba dosent do that (unless i havent figured it out yet.

---

### Post by Carlos Pena on 2009-05-02
The better way to start using the Ubuntu file server is creating a public share with no security restrictions. To do this, just follow these steps: (At the file server console. Login and go to step 1)

1) Create the folder

sudo mkdir /ShareVolume

2) Edit the samba configuration file smb.conf

sudo vi /etc/samba/smb.conf


3) Look for the "share definitions" section and create a public volume. It should look like this:

#================= Share Definitions ================

[MySharedVolume]
comment = Shared Volume on Ubuntu Server
path = /ShareVolume
read only = no
public = yes
create mode = 0777


(Note: Dont delete anything, just insert until this part of the smb file have these lines. 
If you dont know how to use the VI editor, just type i letter, to unlock it and you can insert text)

4) Save the file. (in the Vi editor type these key one by one ESC : w ENTER  : q ENTER
   If everything goes wrong and you want to leave the editor without save, just type  ESC q ! ENTER

5) Restart samba

sudo /etc/init.d/samba restart

Now, in your Windows XP or Vista computers, open "My Network Places", click "Entire Network", then click "Microsoft Windows Network". It will appear the forest you have. By default the Samba create MSHome or Workgroup, just click over it and you will see your server. Click over the server name and you will able to access the volume you create named "MySharedVolume".

I hope this help you. Just let me know. 

Carlos 
Santo Domingo, 
Dominican Republic

---

