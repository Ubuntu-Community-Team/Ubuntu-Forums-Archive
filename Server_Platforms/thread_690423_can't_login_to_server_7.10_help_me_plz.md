---
title: "can't login to server 7.10 help me plz"
date: 2008-02-07
forum: Server Platforms
---

### Post by imax36581 on 2008-02-07
hi my friends
im a newbi in ubuntu
im installing ubuntu server 7.10 and installation finished successfully.
but after installation when i want to login to my sever after entering my username and when i want to enter password my keyboard dont work!!
it seem's that password field is empty.i try all of my keyboard keys but none of them dont work in password field.but i know that my keyboard is ok.its work fine even when i want to enter my username.
please help me.its too bad problem for me that cant login to my server:(

thanks in advance

---

### Post by p_quarles on 2008-02-07
It doesn't "echo" your password when you type it in the console. It still records and authenticates it, though. Just type your password in the field and press enter. You will then be logged in.

---

### Post by freebeer on 2008-02-07
just type the password.  Password fields aren't shown on the screens... you don't even get ***** when you type.  That's normal and a good security feature.

---

### Post by imax36581 on 2008-02-07
o o
im sorry for this simple question :oops:
i said im newbie
i think that at least ubuntu server have a small graphic user interface.
but i see nothing.
can i install gui with some commands?

---

### Post by faulkes on 2008-02-07
> **imax36581 said:**
> o o
im sorry for this simple question :oops:
i said im newbie
i think that at least ubuntu server have a small graphic user interface.
but i see nothing.
can i install gui with some commands?

By default, the ubuntu server edition does not include a GUI (X).

To install the X (GUI/Desktop) you need to issue the following command:

```

sudo apt-get install ubuntu-desktop

```

However, **BEFORE YOU DO THIS**, you should research your computer
to determine what video card you have and your monitor.  As well look at 
or search the forums for posts related to your video card type to see if any
current issues exist.

Faulkes

---

### Post by freebeer on 2008-02-07
You installed the server version, eh?  By default, it doesn't come with a GUI so as to not take up additional resources if you're using it as a traditional server.

To get a GUI, type (or copy/paste):

```

sudo apt-get install ubuntu-desktop

```

This will get you the GNOME desktop.  There are others available, but this will get you going.


meh.. faulkes beat me to it.

---

### Post by imax36581 on 2008-02-07
some where i see this command:
sudo apt-get install xorg
but the xorg package not found

---

### Post by imax36581 on 2008-02-07
yes i install server edition and i download iso file from ubuntu.com
**again ubuntu-desktop package not found**
**faulkes** said that maybe i have a problem...
my graphic card is gigabye geforce 7300gt

---

### Post by p_quarles on 2008-02-07
Can you post the output of this terminal command?:
```
cat /etc/apt/sources.list
```
This could point to the source of the problem.

---

### Post by imax36581 on 2008-02-07
ok
maybe i have to write the output in the paper and then type it here....my god......

---

### Post by p_quarles on 2008-02-07
Or you can write it to a file:
```
cat /etc/apt/sources.list > ~/sources.txt
```
Then upload it here.

---

### Post by imax36581 on 2008-02-07
sorry my friend
i dont know this code and i had to take a picture from my monitor
its not too bad:
[http://i30.tinypic.com/6ivbzp.jpg](http://i30.tinypic.com/6ivbzp.jpg)


thanks for all of helps

---

### Post by p_quarles on 2008-02-07
Hmm. That looks like it should be working. Try the following commands:
```
sudo apt-get update
```
and
```
apt-cache search ubuntu-desktop
```
What are the responses?

---

### Post by imax36581 on 2008-02-08
...for output can you tell some command to ceate txt file that write the output there
i test this:
sudo apt-get update >C:\install.txt
but it said that directory not found
i need command to create a directory.
10x

---

### Post by imax36581 on 2008-02-08
also i test:
apt-cache search ubuntu-desktop
but nothing appeared

---

### Post by cdenley on 2008-02-08
You need to add this line to /etc/apt/sources.list
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
```
You have it configured to only install security updates. Since there is no security updates to the meta package ubuntu-desktop, you won't find it in the security updates. Try this
```

sudo bash
echo deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted>>/etc/apt/sources.list
apt-get update
apt-get -y install ubuntu-desktop
exit

```

> 
sudo apt-get update >C:\install.txt

That's a funny command. Where did you get that from? Windows is the only operating system that I know which uses drive letters. If you want to pipe the output to your home directory, try
```

sudo apt-get update >~/install.txt

```

---

### Post by imax36581 on 2008-02-09
thanks but still** ubuntu-desktop package not found**
any idea?
im tired to switch between windows and ubuntu.plz give me a solution that solve my problem :(

---

### Post by cdenley on 2008-02-09
If you followed my advice, then ubuntu-desktop would be available. You just need the line in /etc/apt/sources.list I had indicated, and an internet connection. It would help if you posted the actual output of the commands I posted, or your /etc/apt/sources.list file (your photo was only part of it). Maybe you should just download the desktop livecd.

---

### Post by imax36581 on 2008-02-09
can you tell me how can i configure my internet connection.maybe its my problem.
thanks

---

### Post by cdenley on 2008-02-09
That depends on your network setup. If you use dhcp, then /etc/network/interfaces should look like this:
```

auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

```
Then, to make changes active, use the command "/etc/init.d/networking restart". However, before you even bother, make sure it isn't already working (it should have been configured during installation).

```

ping -c 1 us.archive.ubuntu.com

```

I still think you should download the desktop cd and start over.

---

### Post by imax36581 on 2008-02-09
im not using dhcp.
now this computer is a stand-alone pc.
what is the connection setting if im not using dhcp?

> **cdenley said:**
> 
I still think you should download the desktop cd and start over.

if i understand,you say i leave server and start desktop edition,isnt it?

i have desktop edition cd,i khow that i must work with desktop edition first.but i want to have a network with ubuntu in my home(one server and two client).
i awnt to work with desktop edition,in adition i want to have a server with ubuntu.

i khow that im newbie in ubuntu...thanks a lot for your answers.

---

### Post by p_quarles on 2008-02-09
@imax36581: The differences between the server edition and the desktop edition aren't all that much. You can install whatever server software you want onto the desktop edition.

---

### Post by cdenley on 2008-02-09
> what is the connection setting if im not using dhcp?
```

man interfaces
man resolv.conf

```

---

### Post by imax36581 on 2008-02-10
> **cdenley said:**
> ```

man interfaces
man resolv.conf

```

thanks for your helps
i try it.
> **p_quarles said:**
> @imax36581: The differences between the server edition and the desktop edition aren't all that much. You can install whatever server software you want onto the desktop edition.

ok....

---

