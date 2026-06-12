---
title: "Problem creating virtual host"
date: 2007-12-06
forum: Server Platforms
---

### Post by andho on 2007-12-06
i added the following line to the /etc/hosts file
127.0.0.1 honors

honors is the name of the virtual host i want created.
now the /etc/hosts file contains:
127.0.0.1 localhost
127.0.0.1 honors
127.0.1.1 andhos

and theres some IPv6 stuff under that.

the problem is when i goto the url:
[http://honors](http://honors)

the page is automatically redirected to:
[http://honors/xampp](http://honors/xampp)
and the page shows 403 forbidden page.

forbidden problem might be due to ownership but why is the page automatically redirected to [http://honors/xampp](http://honors/xampp) ??

and theres another question.
andhos is the name of the computer. why is the ip for it 127.0.1.1

---

### Post by Thensome on 2007-12-06
127.0.0.1 is something called a loopback address. It is used for communication within your computer. If you have a ip address for the internet, you should write that address instead.
If you have installed xampp, you better read the documentation. It redirects for some reason, wild guess is that I would be a welcome page for new installations or config page. I have nerver used it.

---

### Post by andho on 2007-12-07
i know 127.0.0.1 is loopback for the machine but
the machine name is next to 127.0.1.1 instead of 127.0.0.1

> It redirects for some reason, wild guess is that I would be a welcome page
yes /opt/lampp/htdocs/index.html redirects to /xampp/

this is for the localhost and it goes to the xampp control panel
when i enter honors instead of localhost it redirects to [http://honors/xampp](http://honors/xampp) which shows 403 permission denied page instead of the control panel. so im thinking its not a redirect to do with the index file in it

i guess the permission denied problem is because /media/sdc2/andho/websites/honors is not owned by nobody group which apache2 is run as.
the redirect is what i dnt get. the index.php file in 'honors' does not redirect to /xampp/ and if it reads the index.html file in /opt/lampp/htdocs/ then it shud show the control panel right?

PS
i tried to install lampp-server using the command
sudo tasksel install lamp-server

then the console shows a progress bar but it doesnt progress.

---

### Post by Boipster on 2008-01-29
I'm having this issue now, did you ever resolve?

---

