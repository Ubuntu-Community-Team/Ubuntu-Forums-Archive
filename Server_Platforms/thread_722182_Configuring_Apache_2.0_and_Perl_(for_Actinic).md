---
title: "Configuring Apache 2.0 and Perl (for Actinic)"
date: 2008-03-12
forum: Server Platforms
---

### Post by Hopkins on 2008-03-12
I have a question about how to set up perl scripts with Apache 2.0 on my Ubuntu Server 6.06.  I have already spent hours trawling through tutorials and troubleshooting pages to no avail - this post is my last resort!

The server was originally installed minimally (i.e. not in LAMP mode) and I have been using it to add services to as I learn about Linux and have ideas about what I can use it for.  One of the first things I installed was Apache 2.0 (I cannot remember why I chose 2.0 over 1.3 or 2.2) and this has been running well for the last couple of years.  Now, I want to run a piece of catalog software called Actinic on my windows desktop machine and host the results on my Ubuntu server.  The only requirement of Actinic in addition to HTTP is that the server should be able to execute Perl scripts, and this is where my trouble starts!

The first issue I have is that all of the articles I have read seem to refer to httpd.conf - a file that exists on my server only to contain some comment fields saying that it is no longer used.  I have been assuming that I need to use apache2.conf instead.  Also, I have installed some mods - this is the contents of my /etc/apache2/mods-enabled/ directory:

cgi.load
perl.conf
perl.load
userdir.conf
userdir.load

The current addition to my apache2.conf file looks like:

> <Directory /home/steve/sgs/cgi-bin/>
    Options +ExecCGI
    AddHandler cgi-script .cgi
</Directory>

ScriptAlias /cgi-bin/ "/home/steve/sgs/cgi-bin/"

The Actinic catalog uses a setup wizard that runs checks at each stage to help diagnose any problems.  Part of this procedure involves attempting to execute perl scripts, and this is the point of failure.  When I contacted their tech support, they pointed out that the web server is printing the script rather than executing it.  I can point you to my home server so that you can see what I mean:

[http://90.206.97.9/sgs/cgi-bin/](http://90.206.97.9/sgs/cgi-bin/)

Clicking on some of these scripts shows that Apache tries to handle .cgi files but just prints the script instead of running it.  I believe that my problem will be solved if I can make it execute the script!  If I SSH into my server then I can execute the scripts without any problem.

The link above is referring to the following directory on the server:

/home/steve/sgs/cgi-bin/

via a symbolic link to the "sgs" directory stored in:

/var/www/

which is where Apache looks by default.  All of the .pl and .cgi scripts that you can see have the permissions 755 and the .pm files (whatever they are) have permissions 664.

I'm hoping that this is a problem caused entirely by my inexperience and that a veteran of this type of server set up will be able to identify the issue fairly easily!

Thanks in advance for your time.

---

### Post by Hopkins on 2008-03-15
Have I asked something very tricky, or just very dull?!

---

### Post by Hopkins on 2008-03-27
Could someone recommend a forum for troubleshooting Apache problems please?

Many thanks.

---

### Post by Hopkins on 2008-04-11
No harm in one final bump.  I'll go away if this fails!

---

### Post by Hopkins on 2008-05-02
Just in case this is of use to anyone in the future, I can reveal that I have finally solved this, with the help of a friend.  The clue was in the original post.  The Directory statement should referred to the cgi-bin path via the link.  It should have read:

<Directory /var/www/sgs/cgi-bin/>

---

