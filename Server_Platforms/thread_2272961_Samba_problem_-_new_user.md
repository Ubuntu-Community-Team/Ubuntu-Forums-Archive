---
title: "Samba problem - new user"
date: 2015-04-09
forum: Server Platforms
---

### Post by kbelosevic on 2015-04-09
Hello

Im new user to both linux/ubuntu and samba.
Im trying to setup simple file sharing between 1 ubuntu 14.04 lts machine and couple windows 7 machines in my network.
I setup samba following couple instructions using system-config-samba and everything seems to work, i can see shared folders from ubuntu on my windows maching, and shared folders from windows on my ubuntu machine, but my problem is that when i create folder and/or .txt file from windows machine in folder shared from ubuntu (exmpl. defatult home/documets folder) , i can see and acces them on ubuntu machine but i cannot delete both new folder or .txt file, and i cant edit .txt file and save "new" version of it.
And as much as i try to google the solution i cant find anybody with that similar problem.

I dont need special users and password as i will be setting up this server for only home usage, so it should be accesed by everybody connected to my home network via wi fi or lan, for simple storing files,movies,pictures,music and etc.

Thx in advance for help !

---

### Post by sandyd on 2015-04-10
Possible that samba is writing them as the wrong user
Have you set the 'guest user' as your own username in system-config-samba?

Run ```

ls -l
```
in the directory containing those files.

---

### Post by newb85 on 2015-04-10
Welcome!  I think sandyd is onto something...

---

### Post by kbelosevic on 2015-04-10
Thx for welcome !

When i type that command i get :

total 48
drwxrwxr-x 2 kristijan kristijan 4096 Tra 10 13:14 backup
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Desktop
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Documents
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Downloads
-rw-r--r-- 1 kristijan kristijan 8980 Tra  9 21:03 examples.desktop
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Music
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Pictures
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Public
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Templates
drwxr-xr-x 2 kristijan kristijan 4096 Tra  9 21:11 Videos


Maybe problem is that i disabled guest accaunt following tutorial from noobslab website (things to do after installing ubuntu 14.04 lts) using command : 

echo allow-guest=false | sudo tee -a /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

---

### Post by kbelosevic on 2015-04-10
I figured out that when i create 2 files in home/documents, 1. new folder, 2. .txt file on windows 7 machine and then go to my ubuntu machine and go directly to home/documents i can delete both files but i cant edit & save .txt file, but when i go to browse network,servername,documents i can delete both file and edit that .txt file, why is that the case ?

Settings in "samba server configuration" for "server settings" are :
Auth mode :user
Encrypt pass :yes
Guest accaunt : no guest accaunt

Settings for that shared folder "Documents" are :
Directory : /home/kristijan/documents
Share name : documents
Writable:enabled
Visible:enabled
Access : allow access to everyone

---

### Post by sandyd on 2015-04-13
Actually, run the ls -l command in your Documents folder, forgot to mention that.

Run
```

cd ~/Documents
```
before running the ls command

Feel free to remove anything that isn't related to the file

---

### Post by bruce-hyatt on 2015-04-14
I'm no expert but it looks to me like you might need to change permissions to allow group members and/or others to write to the documents directories (folders). Do you know how to read and change permissions?

- Bruce

---

### Post by newb85 on 2015-04-15
Here's my best guess:
When you log into samba from Windows, you're logging in as someone other than kristijan.  The file you create from Windows belongs to that other user, while the directory it's in belongs to kristijan.  Therefore, kristijan can delete or rename the files, but doesn't have permission to edit the file.

You need the directory you're sharing to give read and write permissions to all users who can log in to samba, and have the sticky bit set, so that files and subdirectories in it inherit those permissions.  (Ideally, you do this to a directory other than kristijan's home directory.)

---

### Post by volkswagner on 2015-04-15
Sometimes easy to use does not = easy to setup and vise versa.

Not required, but just a suggestion: If you want "easy" to use, I suggest keeping
file operations to SAMBA. Don't mix file access with samba and direct file access
at Linux desktop or terminal. You need to have an understanding how file permissions 
are handled/enforced and how SAMBA permissions are handled/enforced.

Simple for everyone might mean reduced security and function. If you want everyone
to have the same rights, go ahead and allow everyone to access as guest. SAMBA guest
is not the same as the guest account you disabled for logging in to desktop manager.

I also suggest keeping your shared folders outside of your personal home directory.


Take a look at the "Sample Passwordless Configuration" section in [this link]("https://wiki.archlinux.org/index.php/Samba/Tips_and_tricks").

Do realize the above link is for ArchLinux, so don't try running listed commands. Simply model
your smb.conf like the above referenced config file.

---

### Post by Morbius1 on 2015-04-15
Your best bet is to tell us how you are set up by posting the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

You've been given a number of options here some of which will work and some of which will work only under certain conditions.

*** Setting the guest account to kristen will work I suppose - unless you added the windows user to the samba password database then it will override it.
*** Setting the sgid ( not "sticky" ) bit will certainly work.
*** Not a big fan of a total rewrite of smb.conf for something that's already working but ....

There's even the popular favourite of "force user":

You used system-config-samba to create the share so at the end of /etc/samba/smb.conf you should have something that looks a lot like this:
> [Documents] 
    path = /home/kristijan/Documents 
    writeable = yes 
;    browseable = yes 
    guest ok = yes 
If you edit that file and change the share definition to this:
> [Documents] 
    path = /home/kristijan/Documents 
    writeable = yes 
;    browseable = yes 
    guest ok = yes 
[COLOR=#0000cd]**force user = kristijan**[/COLOR]
Then restart samba:
```
sudo service smbd restart
```
When the remote guest user connects to that share his identity will change to "kristijan" ( for that share ) so when he saves a file / folder it will save as owned by "kristijan". Now both server user and client user can edit the file.

Anyway, it would be better to post the output of the two commands I suggested above to see how you are set up and to make sure there are no conflicts between the classic ( smb.conf ) way of creating shares and the usershare ( Nautilus ) way of creating samba shares.

---

### Post by newb85 on 2015-04-17
> **Morbius1 said:**
> the sgid ( not "sticky" ) 
My mistake.  I read something that used them interchangeably, when they are in fact quite different.

---

