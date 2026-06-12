---
title: "[SOLVED] starting up a ventrilo server"
date: 2008-06-16
forum: Server Platforms
---

### Post by dezeGno on 2008-06-16
Hello there.

I have been trying to set up a ventrilo server, I've got everything up, but i wanted the server to run the server automaticly instead of me having to ssh to the machine and runnig it. 
If i use putty and start the ventrilo server, i can't close putty, because then the ventrilo server goes down.

So how would i get the server to do this automaticly instead of me having to run it from command line?

Thanks in advance and sorry for any spelling errors.

---

### Post by prshah on 2008-06-16
> **dezeGno said:**
> 
So how would i get the server to do this automaticly instead of me having to run it from command line?


Add the command used to start the ventrilo server to your "/etc/rc.local" file. Add it as the last-but-one line, don't disturb the last line ("exit 0")

---

### Post by dezeGno on 2008-06-16
Thanks. But is that all? I've edited the file and saved it, what now? Sorry but I'm kinda new at ubuntu and I'm still learning.

---

### Post by heebus on 2008-06-16
That would be all.  This script is executed when your machine boots up.  That means on boot your server will start.

---

### Post by prshah on 2008-06-16
> **dezeGno said:**
> Thanks. But is that all? I've edited the file and saved it, what now? Sorry but I'm kinda new at ubuntu and I'm still learning.

As heebus said, that should do it. Reboot, check and post back if it doesn't work. If it does, mark this thread as solved: click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

### Post by dezeGno on 2008-06-18
Okay, so I've added the command to start the server in rc.local file, restarted and it didn't startup.

The command to startup the server is ./ventrilo_srv and the server files are located at /home/myaccount/ventrilo

Can any of you tell me what the line should be?

---

### Post by prshah on 2008-06-19
> **dezeGno said:**
> Okay, so I've added the command to start the server in rc.local file, restarted and it didn't startup.
The command to startup the server is ./ventrilo_srv and the server files are located at /home/myaccount/ventrilo



It probably didnt startup since /etc/rc.local runs as root, and not as myaccount. Maybe you should try to add this line```

su myaccount -l -c /home/myaccount/ventrilo_srv
``` Note "su" and not "sudo"

If it doesn't work, some relevant dmesg output will be useful: try```
dmesg | grep -i ventrilo
```

---

### Post by dezeGno on 2008-06-19
> **prshah said:**
> It probably didnt startup since /etc/rc.local runs as root, and not as myaccount. Maybe you should try to add this line```

su myaccount -l -c /home/myaccount/ventrilo_srv
``` Note "su" and not "sudo"

If it doesn't work, some relevant dmesg output will be useful: try```
dmesg | grep -i ventrilo
```

That did not work for me or maybe I'm just not doing it right.

I was able to find this script on the ventrilo.com forums 

```
i had the same problem when i switched my servers to Linux depending on the version of linux i use debian. you would make a file in /etc/init.d or /etc/rc.d named whatever you like. for example i used ventriloserv no file extension needed, then add a script like this.
Code:

 
#!/bin/sh
case "$1" in
start)
echo "Starting Ventrilo Server."
cd /pathtoventrilo/
/ventrilo_srv -d
echo "Ventrilo Server Started"
;;
stop)
echo "Shutting Down Ventrilo Server."
cd /pathofventrilo/
kill `cat ventrilo_srv.pid`
echo "Ventrilo Server Is Now Down"
;;
restart)
echo "Restarting Ventrilo Server..."
cd /pathtoventrilo/
kill `cat ventrilo_srv.pid`
/ventrilo_srv -d
echo "Ventrilo Server Restarted"
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit 0

if you are using the pro version add -Rfilename.reg before -d

then execute this command
Code:

update-rc.d ventriloserv defaults

this will register the script in the init.d if you need to remove it the command is
Code:

update-rc.d -f ventriloserv remove

the script i made has Start Stop and Restart built in it

used like this
/etc/init.d/ventriloserv start
/etc/init.d/ventriloserv stop
/etc/init.d/ventriloserv restart

if you need any other info just ask

- Ethan
```

I have set up that script, but every time i try to run it it gives me an error: 
root@snidugt:~# /etc/init.d/vent start
bash: /etc/init.d/vent: Permission denied

Any help is well taken, and thank you very much.

---

### Post by heebus on 2008-06-19
I assume you gave executable perms to root.

---

### Post by dezeGno on 2008-06-19
I'm not sure, how would i go about doing that :S

---

### Post by dezeGno on 2008-06-20
Okay, so I got this little script going:
```
#!/bin/sh
case "$1" in
start)
echo "Starting Ventrilo Server."
cd ~/ventrilo/
./ventrilo_srv
echo "Ventrilo Server Started"
;;
stop)
echo "Shutting Down Ventrilo Server."
cd ~/ventrilo/
kill `cat ventrilo_srv.pid`
echo "Ventrilo Server Is Now Down"
;;
restart)
echo "Restarting Ventrilo Server..."
cd ~/ventrilo/
kill `cat ventrilo_srv.pid`
./ventrilo_srv
echo "Ventrilo Server Restarted"
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit 0

```

Now, my question is, how do I get vent to run as root with this script?

---

### Post by mbeach on 2008-06-21
Create a file 
/etc/init.d/ventriloserv
```

gksudo gedit /etc/init.d/ventriloserv
```

Paste the text of your script into the file, save and close.

Make sure the code executable.

```
sudo chmod +x /etc/init.d/ventriloserv
```

Then,
```
sudo update-rc.d ventriloserv defaults
```

It will now start on it's own on boot up, or if you want to control it manually, do so with:

```
sudo /etc/init.d/ventriloserv start
```
or stop, or restart

good references
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mbeach on 2008-06-21
but you'll need to change the lines in your script from:
cd ~/ventrilo/

to 
cd /home/yourusername/ventrilo/

or not sure why you can't just have the line:
/home/yourusername/ventrilo/ventrilo_srv

replace the cd and the execution lines.

Good luck,
mb.

---

### Post by mbeach on 2008-06-21
also, I suspect the "-d" after the call to ventrilo is to put it in daemon mode, which you probably want to put back into your script.

mb.

---

### Post by acelin on 2008-06-21
Makes me want to play some DotA...

---

### Post by dezeGno on 2008-06-21
Okay, so i finally got it working, the script i posted was not working for me, so i edited /etc/rc.local 

```
cd ~/ventrilo/
./ventrilo_srv
```

rebooted the server, an that did the trick :P Thank you for all your help.

---

