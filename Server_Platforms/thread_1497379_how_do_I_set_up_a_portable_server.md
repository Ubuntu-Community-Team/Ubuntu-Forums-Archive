---
title: "how do I set up a portable server"
date: 2010-05-30
forum: Server Platforms
---

### Post by nigeldodd on 2010-05-30
Due to hardware failure I have had to set up a server several times. Each time it takes more than a day to set it up from scratch and import the databases etc. I would like a solution that separates all the data, including the configuration files, from the binaries and stores the data on a portable medium that can be quickly used to setup a new server.

Here are the details. I don't use Apache Friends' xampp, instead I set up apache2, php, mysql according to the instructions in [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) 

So the php, css, html etc files are in /var/www, the apache config files are in /etc/apache2 and the mysql data is in /var/lib/mysql

What is the simplest way of making the data and configuration files portable so that I can quickly set up the same server on a new machine that I have first installed Ubuntu on?

Can I put the above mentioned partitions and directories on a usb drive? Should I always make regular dumps of the mysql data and use the dump files instead? Should I keep the whole lot on the local hard drive and find a way using rsync, unison etc to mirror the files onto another potential backup machine on a regular basis - this is not a trivial operation if all the file permissions and ownerships are to be preserved.

---

### Post by Bachstelze on 2010-05-30
That's what things like Norton Ghost are for.

---

### Post by nigeldodd on 2010-05-31
Norton Ghost is a backup program capable of mirroring Windows systems across ftp. I do not think there is a Linux version. If there were a Linux version then it might conceivably provide one of the possible solutions i.e. mirroring. On Linux this can be achieved, with some difficulty, by rsync and/or unison.

I would appreciate any advice on the other solution which involves putting all the data and configuration files on a removable usb drive.

---

### Post by volkswagner on 2010-05-31
There are tons of backup solutions.  You will need to determine what works best for you.

I have used Norton Ghost to create drive images of WinCE and Debian (ReiserFS).

You can look at [PING]("http://ping.windowsdream.com/"), Ghost, [Cloanzilla]("http://clonezilla.org/"), [tar]("http://ubuntuforums.org/showthread.php?t=35087"), etc.

I think for your situation the tar backup method can be great.  You can use it to exclude items not needing backup....very customisable, and can be run on a running system!

Happy searching :)


EDIT:  Forgot to mention [DD]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

---

### Post by The Real Dave on 2010-05-31
Personally, I'd set up the server that I want, databases, configs etc, and then take an image of the partition with Clonzilla. Make a Clonezilla Live USB, and carry the image on that, and you can restore the image anytime you like, with minimal hassle or fuss. There's plenty of howtos on [their site]("http://www.google.ie/url?sa=t&source=web&ct=res&cd=1&ved=0CBkQFjAA&url=http%3A%2F%2Fclonezilla.org%2F&ei=P_sDTLvnKYn40wT-55j3Ag&usg=AFQjCNFZ-xG_6y8Zf7EosJPi7uJXtGOj-g&sig2=cQfEC_HfyQlJ2mP1moGvnw") :)

---

### Post by Chayak on 2010-05-31
Virtual machines are a lot of help that way.  You can make them, keep them updated and then fire it up on just about any x86 hardware with spare memory.

---

### Post by bokcmho on 2010-05-31
This is exactly I did using VMware player to create a new Ubuntu 10.04 server following the guide in Howtoforge.com ([http://howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)). However, since my host system (windows vista) connects to the internet using dhcp, I also need to set up my virtual server with dhcp in order to get update patches.

My questions are:
1. How could I make the virtual server available to be assessed by other PC?
2. Does it work if I change the internet settings in /etc/network/interfaces from dhcp back to static with defined IP?

---

### Post by nigeldodd on 2010-06-01
The posts on clonezilla etc are very interesting. They do allow replication of the complete machine. It might, however, be desirable to be able to transfer just the server data (including apache2 settings, mysql databases, html, php, css files etc) from one machine to another. The target machines might have other uses too and so to replicate the entire machine would preclude that. Also the target machines might have different architectures, 32 bit or 64 bit. 

So what is the minimal amount of reconfiguration that will allow the data (defined above) to be movable from machine to machine? Do I just need to change the settings in my.conf and apache2.conf to point to, say, a removable usb drive that can itself be cloned for backup or moved from machine to machine?

Then, if my machine went down, I could build a new server, make minimal changes to the configuration files so that they point to a usb drive, connect the usb drive and start off from where the dead machine left.

What are the flaws in this idea?

---

