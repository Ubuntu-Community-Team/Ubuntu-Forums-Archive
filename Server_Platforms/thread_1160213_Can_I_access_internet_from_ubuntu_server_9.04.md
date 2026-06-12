---
title: "Can I access internet from ubuntu server 9.04  ?"
date: 2009-05-15
forum: Server Platforms
---

### Post by hoboy on 2009-05-15
I have installed ubuntu server 9.04 on Sun virtualBox on ubuntu host, witch is a ubuntu desktop, I want to install jobss Server on the server installed on the sun-virtualbox.
Is it the only way to get jboss server on ubntu server installed on the sun virtualBox is with scp ? or is there a way to access the internet and downlaod jboss server direct into ubuntu server installed in the sun virtualBox ?

---

### Post by drave on 2009-05-15
just download from the net, as per normal

if your host can reach the internet, then the server guest can

---

### Post by whoop on 2009-05-15
use wget (cli) to download the files directly on to your server.

---

### Post by hoboy on 2009-05-15
> **whoop said:**
> use wget (cli) to download the files directly on to your server.

Please help me out here.
wget (cli) ? I am googling but i have looked in synaptic i can se that wget is installed, but wget (cli) ?
How do I use it ?

---

### Post by whoop on 2009-05-15
> **hoboy said:**
> Please help me out here.
wget (cli) ? I am googling but i have looked in synaptic i can se that wget is installed, but wget (cli) ?
How do I use it ?
Well I assumed you want to download something with your server. A server usually does not have a window manager. So you need a command line interface (cli) application that can download stuff from the internet. You can use wget for this.
type:
```

man wget

```
in your terminal and all should be clear.

---

### Post by hoboy on 2009-05-15
> **whoop said:**
> Well I assumed you want to download something with your server. A server usually does not have a window manager. So you need a command line interface (cli) application that can download stuff from the internet. You can use wget for this.
type:
```

man wget

```
in your terminal and all should be clear.

sorry to bother
shall I run the wget command on the host ? or on the server runing on the virtualBox ?
man wget this command should be run on the server not on the host ?

---

### Post by dtoronto on 2009-05-15
use the wget command or you could just download it to your desktop/laptop and FTP it over to your server.  either way I think you are making this way more difficult than it needs to be.

---

### Post by dtoronto on 2009-05-15
Sorry, forgot to mention

Yes all commands and performed need to be run from the Command Line Interface of your virtual server.

---

### Post by whoop on 2009-05-15
> **hoboy said:**
> sorry to bother
shall I run the wget command on the host ? or on the server runing on the virtualBox ?

Well if your goal is to have a file from the internet on your server you should of course use it on your server. Like:
```

wget <file you want to download>

```
Example
```

wget http://mirrors.cat.pdx.edu/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso

```
this downloads the ubuntu 9.04 desktop iso to the current directory
> **hoboy said:**
> 
man wget this command should be run on the server not on the host ?
Doesn't matter. man is a package that gives you descriptions of other packages. So you can type man <any command> to find out more about <any command>
example:
```

man wget

```
this outputs:
```

NAME
       Wget - The non-interactive network downloader.

SYNOPSIS
       wget [option]... [URL]...

DESCRIPTION
       GNU Wget is a free utility for non-interactive download of files from
       the Web.  It supports HTTP, HTTPS, and FTP protocols, as well as
       retrieval through HTTP proxies.

       Wget is non-interactive, meaning that it can work in the background,
       while the user is not logged on.  This allows you to start a retrieval
       and disconnect from the system, letting Wget finish the work.  By
       contrast, most of the Web browsers require constant user&#8217;s presence,
       which can be a great hindrance when transferring a lot of data.
ETC.........

```

Hope this helps.

---

