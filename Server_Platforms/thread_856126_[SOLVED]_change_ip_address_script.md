---
title: "[SOLVED] change ip address script"
date: 2008-07-11
forum: Server Platforms
---

### Post by brocky102 on 2008-07-11
Is there any way to change the ip address of a server by a script which is run by a web browser. What I have is an installation web page which sets up different settings, all of which i need root access for. Does anyone have any ideas on the best way to do this?

---

### Post by justleen on 2008-07-11
tricky.. Since you need rootrights from a webpage..
all i can think of at the moment would be trough a root-cron script that checks for content created by the web page.. 

What you could do, is the webpage wirte to a file which it has access to. in that file you have to date, one of the last change and one of the requested change (that will be when you saved)
changed=<unixtime>
requestedchange=<unixtime>
ipaddress=<ip>

then have a root cron script that compares the dates, if they are different, you want to change the ip address. once change, update so that the dates are the same again.


or..


have a webpage that creates a file "change ip"
have a root-cron script that checks if that file exist, if so change the IP and delete the file.

maybe, you can change you sudoers file to give the apache user right to the "change ip command" that would grant apache root rght on that specific command

---

### Post by hyper_ch on 2008-07-11
well, I'd go for something like justleen... but I would make ths change

(1) you need to create two files by the webbrowser
- a new interfaces config file
- a "update" file

(2) then you make a script that
- checks if the update file exsist
  - if it exists, cp -f the new interfaces config file to /etc/network/interfaces
  - restart networking
  - delete that update file
- if the update file does not exist, then don't do anything

(3) add that script to cron

---

### Post by brocky102 on 2008-07-11
that is an option but i don't really want to do it as i want the changes to be instant as it will be on a commercial product. would it possible to add apache/httpd as a member of the root group? isn't this how webmin does it?

---

### Post by carcdrcdr on 2008-07-11
It sounds like you know how to write the script you want so I'll skip right to the good stuff!!  

Use SUDO:
man sudo

From there you can just set up your /etc/sudoers (with visudo -f /etc/sudoers)

And add this line: (replace user with the user you need)
user ALL = NOPASSWD: /usr/sbin/ifconfig

Now in your script you can just do: (this is an example)
sudo ifconfig eth0 $IP

What this does is let you run ifconfig with root privs with out entering a password.  For securities sake please give your 'webapp' proper checks to stop abuse!
;)

And to answer your question, no webmail  does not get ROOT privs EVER EVER EVER! ;)

That should do it!

---

### Post by brocky102 on 2008-07-12
thanks carcdrcdr that worked great. btw i wasn't talking about webmail having root access i was talking about webmin the browser based management system for linux

---

