---
title: "How to find out &quot;how&quot; a program is launching automatically at startup?"
date: 2015-12-21
forum: Server Platforms
---

### Post by suaro on 2015-12-21
Hi Experts,

- Ubuntu 14.04 LTS (server)

My system has a program that is started automatically when the system boots.  I'm trying to find out how this program is started so I can change the command line. 

Here's the program of interest:

PID: 18656
User: root
Parent Process: /sbin/init

Command:
sudo stdbuf -oL -eL /usr/bin/anaconda/bin/jupyter-notebook --config=/var/lib/.jupyter/jupyter_notebook_config.py


A process or script is launching the above command and I'm trying to find out where this is happening so I can make change to the command line params. 

I've looked in /etc/init directory but I don't see any configurations in there that would invoke this. 

Tips appreciated!

---

### Post by howefield on 2015-12-21
Thread moved to the "*Server Platforms*" forum.

---

### Post by ian-weisser on 2015-12-21
Try the 'pstree' command. It may offer useful insights.

Also look in /etc/init.d/ for more boot scripts.
Are you sure it starts at *boot* (between POST and Login)? If it starts after login, look in ~/.config/autostart and ~/.config/upstart

---

### Post by suaro on 2015-12-21
Thanks for the reply.

I logged in as root and changed to the ~/.config directory and this folder is empty. Check for hidden files and dirs also
Its possible the script starts after boot but not sure where to look though.

Below, the awk, python and sudo operations occur from the root user account and the parent of process below is /sbin/init  

init(1)-+-acpid(1571)
        |-awk(38812)
        |-python(37638)
        |-sudo(38813)---jupyter-noteboo(38816)
            . . . 
                 . . . 

If I kill -9 each of the processes above, they will disappear and then shortly come back with new pids. 

I would think if an agent or some processes was monitoring and then re-spawning ,  the parent ID of the spawning process would be noted in ps util.   According to ps util the parent is init(1) so maybe a monitoring agent was launched at boot.   

I've scoured /etc/init.d folder for clues but unable to find which process is spawning these apps. 

The **/var/log/auth.log** even details the time the operation occurs but leave no evidence of which process did this or where this came from.   

   Dec 21 15:18:36 srv1057 sudo:     root : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/usr/bin/stdbuf -oL -eL /usr/bin/anaconda/bin/jupyter-notebook

---

### Post by ian-weisser on 2015-12-21
Could be that init is respawning those jobs...in which case there *must* be a script in /etc/init.d or .conf in /etc/init...

OR perhaps dbus is triggering them.
Take a look in /usr/share/dbus-1/services/*

Another option is to do a big, long recursive string search to find a file with that "sudo stdbuf -oL -eL /usr/bin/anaconda/bin/jupyter-notebook" command (if it's coded as a string):
[http://unix.stackexchange.com/questions/16138/how-to-search-text-throughout-entire-file-system](http://unix.stackexchange.com/questions/16138/how-to-search-text-throughout-entire-file-system)

---

### Post by suaro on 2015-12-21
Thanks. 
I ran the following :

find / -xdev -type f -print0 | xargs -0 grep -H "sudo stdbuf -oL -eL"

...and got a hit.  I can see the py script constructs most of the parameters programmatically and issues an   os.system("""   ... call the spawn. 

I can see where this particular python app ties back to a process in the init.d so I think I'm good !

Thanks for the help !!

P.S.  I wonder why the OS reports init(1) as the parent process rather than name of the program that actually starts the processes?  Probably lots of internals I don't know about :) but it would have been really easy to narrow down had it said abc.py **-> **sudo stdbuf -oL -eL .....

---

