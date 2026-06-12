---
title: "Require password for Ubuntu server 12.04"
date: 2013-10-22
forum: Server Platforms
---

### Post by Daniel_Burnett on 2013-10-22
I started working at a small office that had Ubuntu Server 12.04 installed by someone else a while ago. I'm very familiar with Windows but don't know much about servers or Linux. We have a new client who requires us to password protect our file server. I've looked around but I'm so unfamiliar with this I'm completely lost. Can anyone help me set this up?

---

### Post by ian-weisser on 2013-10-22
Wait...so when you boot the server, you don't get a login prompt?
Is everybody there using the same account on the server?
Does that mean all the services are also running as that user?

---

### Post by Daniel_Burnett on 2013-10-22
Thanks for the response.  There's no login prompt.  GUI is not installed either if that matters.  Everyone is using the same account, it's just a file server.  We need to make it so if any client computer on the network tries to access the file server they are given a login prompt.

---

### Post by SeijiSensei on 2013-10-22
When you say "access the server" do you mean access it using Windows networking, or are the client workstations running Linux or some other Unix derivative?  My guess is the former.  If that's the case, you'll need to reconfigure the "Samba" server that supports Windows networking.   Let us know what you mean by "access," and then we can talk about securing the server.

---

### Post by Daniel_Burnett on 2013-10-22
Sorry for not being more clear.  I mean accessing it using Windows networking.  Our client workstations are using Windows 7 Pro.

---

### Post by SeijiSensei on 2013-10-22
I was afraid of that.  Handing users and passwords in Samba can be a bit tricky for the uninitiated.

First, every user must have an individual account on the Linux machine as well as an account in Samba.  The easiest solutions require use of the command line with root privileges via the "sudo" command.  To add user "shirley" to the Linux OS, open a Terminal and run the command:

```
sudo adduser shirley
```

You'll be prompted to enter a password for shirley.  You can avoid creating a password for her by simply hitting enter at the Password: prompts repeatedly until the script gives up, then accepting the entry.  The dialog should look something like this:

```

$ sudo adduser shirley
Adding user `shirley' ...
Adding new group `shirley' (1001) ...
Adding new user `shirley' (1001) with group `shirley' ...
Creating home directory `/home/shirley' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
passwd: Authentication token manipulation error
passwd: password unchanged
Try again? [y/N] n
Changing the user information for shirley
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] y

```

That creates an entry for shirley in the /etc/passwd file but places a "!" in the encrypted password field in the file /etc/shadow where passwords are actually stored.  The number in parentheses like "(1001)" is her unique numeric user ID.  New users will get different IDs in ascending order.  Shirley now has an account on the machine but cannot log into Linux.

Now you need to create an account for shirley on the Samba server using its "smbpasswd" program like this:

```

$ sudo smbpasswd -a shirley

```

You'll be prompted twice for the password.  Now check to see if shirley can log into the server.  You may also need to make some changes in the way the shared directory is configured.  Each share is defined in the /etc/samba/smb.conf file; the definitions begin with the share name in brackets.  So if you had a share that you access from Windows as \\server\office, you would look for the lines that begin with "[office]" in smb.conf.  Please post the contents of the share definition here starting with the bracketed name and ending at the next bracketed name or a comment line whichever comes first.  Use the [noparse]```

```[/noparse] tags to preserve readability.

---

### Post by Daniel_Burnett on 2013-10-23
Thank you for all the info.  Much appreciated.  I'll have to mess around with this to see what I can get working.

---

