---
title: "is intrepid safe -&gt; apache2=php5+mono"
date: 2008-10-30
forum: Server Platforms
---

### Post by Vegan on 2008-10-30
I have phpBB so I am hinked up trying to use xsp2 again. Now I have 8.10 on the box and was pondering a move with xsp2 again.

goal is to have apache2 capable to working with *.* web pages with catch all for which interpreter is needed.

---

### Post by alienprdkt on 2008-10-30
well apache 2 / php/ perl / python works!!)

don't know bout mono, trying to get away from MS with their .asp(x) .vb 

~can't blame you for asking is it safe???(after your past couple days)~

---

### Post by directhex on 2008-10-31
I wrote a guide & tried to add it to the "Tutorials & Tips" forum. Evidently someone is suppressing it. I'm not bothering to retype it.

Short version: install libapache2-mod-php5, install mono-apache-server2, install libapache2-mod-mono, run "a2dismod mod_mono", run "a2enmod mod_mono_auto", and run "ln -s /usr/bin/mod-mono-server2 /usr/bin/mod-mono-server". Both ASP.NET and PHP files will be served fine from /var/www with no further configuration. If you want more fine-grained control, then switch back from mod_mono_auto to mod_mono, delete that symlink from earlier, and look in /etc/mono-server2 for per-site configuration.

---

### Post by Vegan on 2008-10-31
i configured apache2 to serve from /web but otherwise its default. I simply use /web as its a short easy path that is shared in samba as well.

I will gamble with your idea and get back here if it blows again.

---

### Post by Vegan on 2008-10-31
Minor problem:

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod_mono_auto.lo
ad: Cannot load /usr/lib/apache2/modules/mod_mono.so into server: /usr/lib/apache2/modules/mod_mono.so: cannot open shared object fi
le: No such file or directory
   ...fail!



I am using the default unmodified apache2.conf file, I put my stuff in hpptd.conf.

---

### Post by alienprdkt on 2008-10-31
aye', Vegan,

Don't know if you are going to (or still looking for an easier atempt to) try and get dns going with BIND, but I came across this yesterday,  [shortest bind how to I have ever saw]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/")!

---

### Post by directhex on 2008-10-31
> **Vegan said:**
> Minor problem:

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod_mono_auto.lo
ad: Cannot load /usr/lib/apache2/modules/mod_mono.so into server: /usr/lib/apache2/modules/mod_mono.so: cannot open shared object fi
le: No such file or directory
   ...fail!

At your end. Check your disk for problems, because /usr/lib/apache2/modules/mod_mono.so is categorically in the libapache2-mod-mono package

---

### Post by Vegan on 2008-10-31
I reinstalled that component, cured the error.

So now, extending the show to the next phase, mono-common safe?

---

### Post by directhex on 2008-10-31
> **Vegan said:**
> I reinstalled that component, cured the error.

So now, extending the show to the next phase, mono-common safe?

I already told you it was, and you already have it installed (it's a dependency)

Any problems you believe were caused by mono-common were imaginary - your problem was caused by removing libapache2-mod-php5 due to a broken dependency in Hardy

---

### Post by Vegan on 2008-11-01
I am not yet familiar with all of the dependencies, but I am slowly accumulating a knowledge base I can post on my site for people to use.

Next up is the cli, for programming language support, is it already included with the components I have?

---

### Post by directhex on 2008-11-01
> **Vegan said:**
> I am not yet familiar with all of the dependencies, but I am slowly accumulating a knowledge base I can post on my site for people to use.

Next up is the cli, for programming language support, is it already included with the components I have?

What *precisely* do you mean by "the cli"? You need to be very specific here because the abbreviation "CLI" has two possible meanings when talking about Mono

---

### Post by Vegan on 2008-11-01
Over in the Microsoft world, CLI refers to common language interface, a basket of functionality that is used by Microsoft's .NET programming languages C# and VB along with a huge bunch of 3rd party languages.  At least 15 of them last time I reviewed the range and likely many more by now, as I did that 4 years ago.

mono provides some of the base functionality. Somewhere I saw a cli-????? module, forget where as I forgot to bookmark the site.

mono seems to be real basket of functions, and I am unclear as to what I need to enhance my web server.

A goal, is to serve AJAX documents, which calls for both server side and client side code. 

Being a web-master of a Linux server with a Windows machine as the development box, makes for complicated situation. Thankfully SAMBA makes it easy to share the web root and I can map the Linux directory into Windows as a drive letter. Windows development tools recognize the share as a server.

Adobe Dreamweaver supports PHP, Microsoft Expression Web does barely. Microsoft Visual Studio is clumsy with MySQL meaning some Linux script is better adapted.

The holy grail, to use anybody's web page development tool, 3rd party script and use them all in a heterogeneous fashion. Messy I know.

:guitar:

---

### Post by directhex on 2008-11-01
Off the top of my head, Ubuntu 8.10 provides required stuff for the following CLI languages:

C# (mono-gmcs package)
JScript (mono-mjs package)
Nemerle (nemerle package)
Boo (boo package)
Java (ikvm package)
Python (ironpython package)

Others may work, but are not packaged in any stable Ubuntu release (e.g. I have VB.NET packages here which missed Intrepid, but will be in Jaunty)

I have no idea how to use any of the above in ASP.NET pages though, i have no real ASP.NET experience

---

### Post by Vegan on 2008-11-01
In an ASPX page the general idea is using the:

<script language="C#" runat="server">
// your code here
</script>

Its automated in Microsoft professional development tools.

---

