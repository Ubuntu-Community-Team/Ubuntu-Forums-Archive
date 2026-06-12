---
title: "Need help setting up a server"
date: 2011-06-30
forum: Server Platforms
---

### Post by afeng on 2011-06-30
Hi all,

My dad asked me to set up a server for his office, and here I am two days later confused as hell. I have a bit of experience with the linux environment and using the terminal but beyond that, I'm as green as they come!

The server is supposed to (minimally) be able to backup the half dozen Windows laptops in the office and to handle all the printing jobs. The setup I tried so far is having a wireless router connected to the DSL line, and the machine running the server attached to the router's LAN. So the router is doing all the DNS/DHCP stuff. All I've gotten out of the server so far is being able to open a SSH connection to it with putty on the laptops and get the web browser to display "It works" whenever I type in the host name.

Most guides I've seen tell me that the server should handle the DNS/DHCP stuff, but would I need another network card to get it to work that way? I'm thinking that the server should be directly connected to the DSL line and the router should just act as a bridge giving wireless access to the laptops. I'm running into a lot of problems and difficulties setting up samba and backuppc so I'm wondering if the overall layout of the network might be the cause?

Any advice would be appreciated, thanks.

---

### Post by tgm4883 on 2011-06-30
I recommend installing a solution to make this a little easier on yourself.

Look into using Ebox (or possibly Zentyal, which is just Ebox integrated into Ubuntu 10.04)

---

### Post by sdmike6 on 2011-06-30
You would only need another nic card if you have a console setup. So if you look yourself out of the server you can go through the console and get back in. 

As far as samba goes what are you having trouble with? 

this is a great article on how to setup samba: 

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

---

### Post by afeng on 2011-06-30
> **tgm4883 said:**
> I recommend installing a solution to make this a little easier on yourself.

Look into using Ebox (or possibly Zentyal, which is just Ebox integrated into Ubuntu 10.04)

Well that causes more questions than it answers. Is Zentyal basically an installation wizard? And will it work regardless of the layout of the network? I imagine using this solution wouldn't be quite as good a learning experience (read: resume filler ;))as setting up an Ubuntu server from scratch.

---

### Post by afeng on 2011-06-30
> **sdmike6 said:**
> You would only need another nic card if you have a console setup. So if you look yourself out of the server you can go through the console and get back in. 

As far as samba goes what are you having trouble with? 

this is a great article on how to setup samba: 

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Sorry what do you mean by console setup? Do you mean Ubuntu setup without the desktop and everything is in the command line?

I followed the setup instructions for samba, but now I'm having trouble getting it to work. I'll go over to a laptop and tell it to print some document on the printer attached to the server and nothing happens. When directly connected to the printer it print fine, but now the printing job just sits in queue. I assume the pc doesn't know how to get the job over to the server or something like that, which is why I"m worried so much about the networking setup.

---

### Post by gordintoronto on 2011-06-30
Just because it is a "server," doesn't mean that Ubuntu Server is an appropriate solution. Ubuntu Server is good for high-volume web sites, not so good as a usable system.

Install Ubuntu Desktop. Set up some folders which are shared. Add a printer, and share it. Much, much easier with a GUI.

---

### Post by LtPitt on 2011-07-01
We need further details on which kind of services you want to offer to users.

As far as I've understood you need centralized backup?

For their documents only?

Of an image of their pc?

Why is webserver involved, then?

Give details about what you want to do (pratically) and we'll try to help :)

---

### Post by SeijiSensei on 2011-07-02
Let's start with the backup task.

On the laptops, make sure that the folders that need to backed up are shared with Windows networking.  

Now, on the Linux box, install the **smbfs** program.  This will enable you to mount the exported Windows shares onto the laptop.  If you want to use symbolic hostnames instead of IP addresses to identify the laptops, make sure there's an entry in /etc/hosts for each laptop.  

In /etc/hosts:
```

10.10.10.10     laptop1
10.10.10.11     laptop2
[etc.]

```

Replace "laptop1" with the name of the computer at 10.10.10.10, etc.

Now create a "mount point" (just a directory) under /mnt with sudo where you'll mount the laptop's files for backup like this:

```

sudo mkdir /mnt/laptop
sudo smbmount //laptop1/exported_share /mnt/laptop [-o options]

```

The options can include a username and password if one's required to access the laptop's files (run "man smbmount" for details).  Replace "exported_share" with the name of the share on the laptop where the files to be backed up are stored.  (Use "smbclient -L laptop1" to see a list of laptop1's exported shares.)  You should be able to see the laptop's files by running "ls /mnt/laptop".

If everything is working as expected, try backing up the laptop's files with rsync like this:

```

sudo mkdir -p /backup/laptop1
cd /mnt/laptop
sudo rsync -av . /backup/laptop1

```

rsync will report the files it's backing up (the "v" option); they should appear in /backup/laptop1.

You can write a simple bash script to automate this procedure along these lines:

```

#!/bin/bash

# allow each laptop to have one or more exported shares
LAPTOPS="laptop1/share1 laptop1/share2 laptop2/share laptop3/share"

# keep a log for reference
LOG=/var/log/laptop-backup

# make sure nothing is mounted at /mnt/laptop when we begin
umount /mnt/laptop 

for L in $LAPTOPS
do

     smbmount //$L /mnt/laptop  # plus any options if needed
     cd /mnt/laptop

     # create a local directory for each share if it doesn't exist
     mkdir -p /backup/$L

     # run the backup
     cd /mnt/laptop
     echo "Beginning backup of $L at $(date)" >> $LOG
     rsync -av . /backup/$L >> $LOG
     echo "Backup of $L completed at $(date) >> $LOG
     umount /mnt/laptop

done
exit 0

```

This gets trickier if each exported share is owned by a different Windows user.  If the laptops have an active Administrator account and a common admin password, you could use that.  Otherwise, resolving the authentication problem is "left as an exercise" as the textbooks say.

Create a file as root with sudo like /usr/local/sbin/laptop-backup, put the code above into it, and make it executable:

```
chmod u+x /usr/local/sbin/laptop-backup
```

Finally, use "sudo crontab -e" to edit root's "crontab" file and create a scheduled backup like this:

```

* 1 * * * sh /usr/local/sbin/laptop-backup

```

(By default, you'll probably find yourself in the "vi" editor.  If you'd prefer to use nano or emacs, set the EDITOR environment variable first by running "export EDITOR=nano").

This will run the script each day at 1 am.

This is a lot to digest, but, to be honest, your Dad gave you a rather difficult task as your first exposure to Linux server administration.

---

### Post by drdos2006 on 2011-07-02
You are going to have to do some heavy reading to set up your first server.
Zentyal will get your fathers machine running in an office environment while you learn the more detailed operations of a server. [http://www.zentyal.com/](http://www.zentyal.com/)
.....................
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by HermanAB on 2011-07-03
As a wise person up above said: 
Use ordinary Desktop Ubuntu. Set up sharing and printing - done.

Ubuntu Server edition is for headless machines doing unspeakable things in a dark corner of a dank data centre.  It is not what you need.

---

