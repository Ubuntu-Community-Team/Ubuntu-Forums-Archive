---
title: "Server - Monitor: CPU%, RAM%, DISK %, HEAT °C, PROCESS"
date: 2013-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Selcuk_Demirci on 2013-08-10
Hello all,

I'm looking for a mix of New Relic & Htop in the terminal of the server.
I would like to have an overview like htop, monitoring:

ONE overview with all these information in terminal
- CPU all core's usage & history (Graph )
- RAM usage & History (Graph)
- Heat in °C & History (Graph)
- Disk Usage in GB's
- Uptime & Uptime history, Boot, Shutdown and restart history 
- See Processes: TOP10 most using processes and/or all processes
- External IP address
- Internal IP address
- Logged in Users
- Free up inactive RAM option
- Killing processes easily
- See live available update counts


I know there isn't such thing as this but wouldn't be great to have a program like this?
In the hope some dev will find this interesting and would like to invest some time to do a great job for the community i'm posting this.
And to use a command like htop for example: sutop :KS


Greetings, let me know your thoughts about this one.

---

### Post by karan_sharma3 on 2013-08-10
nice performance i seem it is very nice thing .

---

### Post by Selcuk_Demirci on 2013-08-10
Actually i found a couple of alternatives on htop... but it's not what i want...


**Glances** 
[I]is an example
[/I]____________________________________________________________________________________

[IMG]http://cdn.linuxaria.com/wp-content/uploads/2013/02/glances2.png[/IMG][I]

sudo apt-add-repository ppa:arnaud-hartmann/glances-stable[/I]
*sudo apt-get update*
[I]sudo apt-get install glances
glances

[/I]**Htop** 
[SIZE=1][I]is an example 
[/I][/SIZE]____________________________________________________________________________________
[IMG]http://cpuchip.net/wp-content/uploads/2012/05/htop-screenshot.png[/IMG]

apt-get install htop
htop



**Libstatgrab** 
[SIZE=1][I]is an example 
[/I][/SIZE]____________________________________________________________________________________

[IMG]http://software.opensuse.org/package/screenshot/saidar.png[/IMG]
sudo apt-get install libstatgrab6



**Saidar** 
[SIZE=1][I]is an example 
[/I][/SIZE]____________________________________________________________________________________

[IMG]http://www.klein2.de/wp-content/uploads/2013/04/saidar.png[/IMG]
sudo apt-get install saidar
saidar

---

### Post by Boab1993 on 2013-08-10
Most of this information already on the system in different files, except say the graphs.
Its just a case of getting it all together and making it look nice and make sure it works properly

Im sure someone will be enthusiastic enough to make something

---

### Post by 3rdalbum on 2013-08-10
> **Boab1993 said:**
> Most of this information already on the system in different files, except say the graphs.
Its just a case of getting it all together and making it look nice and make sure it works properly

Im sure someone will be enthusiastic enough to make something

You want a button to "free up inactive RAM"? Why, do you want the program to run on Windows?

---

### Post by Boab1993 on 2013-08-11
> **3rdalbum said:**
> You want a button to "free up inactive RAM"? Why, do you want the program to run on Windows?

Did i just experience my first linux joke?

A momentus occasion. Time to denote it in the most unsophisticated way possible: =D

---

### Post by Selcuk_Demirci on 2013-08-24
[COLOR=#000000]It's very rude to demotivate me and to act like a Microsoft guy.
Maybe you didn't know the command: [/COLOR]echo 3 > /proc/sys/vm/drop_caches

---

### Post by kosmokramer314 on 2014-02-21
thanks for posting this..I didn't know about glances and it's pretty nice to have!

---

### Post by cariboo on 2014-02-21
Another thread the auto close script missed. I you want to add to the discussion please start a new thread, as this one is closed.

---

