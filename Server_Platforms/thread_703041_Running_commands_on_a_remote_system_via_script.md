---
title: "Running commands on a remote system via script"
date: 2008-02-20
forum: Server Platforms
---

### Post by smegly on 2008-02-20
Hi Guys,

I have several linux machines that i want to run sparatic updates on via a shell script I write on the main machine. The problem I have is that when i ssh into the remote server - none of my script commands work (as it's stuck in the ssh command on the script) I can type anything on the remote server and when i type exit to leave the remote server the rest of the script is run.

Here is an example shell script to detail whats happening. 

```
echo 'Testing Script'
ssh ct.servebeer.com
cd /tmp
wget http://www.craventechnology.com.au/images/hm_banner.jpg
cp hm_banner.jpg /var/www/html/craven_technology.jpg
exit
echo 'test completed'
```

In this script the ssh ct.servebeer.com connects fine but simply waits at the prompt. When i type exit the following commands are run on my local machine not the remote machine. 

Any ideas on how i can create a script and run it locally for it to connect to my remote servers and issue the commands I want?

Cheers,

Matt

---

### Post by Mr. C. on 2008-02-21
You're going about this the wrong way.

Create the script on the server, containing the commands you want run.

Then, do:

```
ssh server myscript
```

Alternatively, you can pass your commands as SSH arguments, as in:


```
ssh server 'ls ; who; ps'
```

MrC

---

### Post by smegly on 2008-02-24
Ok, -- so if i'm correct I can run a script that looks like this?

```
echo 'Testing Script'
ssh ct.servebeer.com wget http://www.craventechnology.com.au/myScript.sh
ssh ct.servebeer.com myScript.sh
echo 'test completed'
```

With myScript.sh containing all the commands I want to run on the remote machine? 

Since I will have lots of machine I dont want to login to each machine and create the script.

Will this work? 

I will test and see what happens :D

Cheers,

Matt

---

### Post by Mr. C. on 2008-02-24
The approach you are taking may be a bit circuitous, but I'm not exactly clear 

If all you are trying to do is download the file and have it renamed, you can use the -O option to output the file to a named file:
```

ssh ct.servebeer.com wget -O /var/www/html/craven_technology.jpg http://www.craventechnology.com.au/images/hm_banner.jpg  
```

But this obviously works for the single named file used in your example.

If you have a number of systems, say A, B and C, and you want to run that exact same script on each, you can either copy the same script to each system, and then run the script:
```

   ssh A /path/to/myscript
   ssh B /path/to/myscript
   ssh C /path/to/myscript

```
or if myscript is trivial enough, you can pass the command sequence to ssh as command line arguments as in:

```
  ssh A 'wget -O localfilename [http://remotehost/filename](http://remotehost/filename)'
  ssh B 'wget -O localfilename [http://remotehost/filename](http://remotehost/filename)'
  ssh C 'wget -O localfilename [http://remotehost/filename](http://remotehost/filename)'
```

And of course, either version of these can be done more simply as:

```
  for host in A B C ; do
     ssh  $host /path/to/myscript
  done
```

or

```
  for host in A B C ; do
     ssh $host 'wget -O localfilename http://remotehost/filename'
  done

```

Again, these are simple examples, and depending upon your needs, your myscript can be as simple or complex as necessary, and even accept its own command line arguments so that you can make the script work for the general case of a single file, multiple files, etc.

But first, consider defining your requirements a bit more.

The problem with your initial attempt was a confusion in thinking that commands you enter in a script that follow an **ssh** are interpreted by that remote shell.  This does not do what you were thinking:

```
#!/bin/bash
ssh remotehost
hostname

```
will **not** output the hostname of the remote host.  Rather, when you execute **myscript** (that contains the above commands), a new (sub)shell is started, which begins reading its list of commands from the script.  The first command in that script is the **ssh** command, so the subshell starts a new command (**ssh**) and that creates a connection to the *remotehost*.  BUT... until you **exit** that **ssh** session, which is reading your keyboard input (STDIN), the **myscript** commands cannot continue.  When you do **exit** the ssh session, commands resume at the point in **myscript** immediately after the **ssh** (which itself is just a command).  At that point, the **hostname** command will run, and your current host's name will be output.

MrC

---

