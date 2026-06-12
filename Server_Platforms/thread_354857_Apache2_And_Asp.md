---
title: "Apache2 And Asp"
date: 2007-02-06
forum: Server Platforms
---

### Post by kimvall on 2007-02-06
Hello, my ISP doesn't like my SQL scripts (too heavy for them) so I thought I'd try to install and run it on my Ubuntu machine at home, which I access only via SSH.

sudo apt-get -y --force-yes install apache2
sudo apt-get -y --force-yes install libapache-asp-perl
sudo apt-get -y --force-yes install php5
sudo apt-get -y --force-yes install mysql-server
sudo apt-get -y --force-yes install phpmyadmin

I then copied the ASP files to the www-directory but when I try to access it, the ASP is just shown, and not interpreted.

[http://pushead.ath.cx/sowhatisthedeal.com/records/default.asp](http://pushead.ath.cx/sowhatisthedeal.com/records/default.asp)

Perhaps this has something to do with MIME types? Any clues anyone? I fairly new to Linux.

---

### Post by kidders on 2007-02-06
Hi there,

Have you installed an ASP extension for apache?

---

### Post by kimvall on 2007-02-06
No I haven't, I had no idea it was needed! What's the name of the package? I've searched apt-get for it, but can't seem to find it.

---

### Post by Fundi on 2007-02-06
I think its called mono-apache-server but im not sure.

---

### Post by kidders on 2007-02-06
Ohhh... you mean you haven't done this before?

Apache/Linux and ASP are fundamentally incompatible really, so I wouldn't expect getting them to play nice together to be too easy. Google seems to turn up some promising possibilities, though.

Is it too late (ie have you done too much work) to switch to a more standard language? You see, using ASP will presumably open your Linux box up to all Microsoft's lovely security holes. I'm also guessing that you won't necessarily be able to get your scripts to work unaltered with Linux.

**Edit:** Would [http://www.apache-asp.org/](http://www.apache-asp.org/) be any use?

---

### Post by kimvall on 2007-02-06
The scripts have already been written, so I am essentially just migrating them from my ISP, to my Lunix machine at home.

Thanks for the direction, now I know how to get on with this little project.

---

### Post by conjur3r on 2007-02-08
Did your ISP run IIS or apache?

If it was IIS, then forget it!  The freely available interpretors that allow you to run native ASP code on *nix will do it but won't do everything.  They all have problems.  Apache ASP is not based on vbscript like you think it would.  It actually uses Perl syntax so you'll have to rewrite your scripts.

When I was researching into this before, the best solution at the time was Chilisoft ASP but even then, it didn't support everything in ASP (for example, no class support).  I believe Sun now owns it so who knows if it's made roadways.  [http://www.sun.com/software/chilisoft/](http://www.sun.com/software/chilisoft/)

My preference would be to leave ASP where it belongs (on microsoft IIS).

---

### Post by kimvall on 2007-02-08
Yeah, I'm kinda leaning towards that idea too.

---

### Post by scrupul0us on 2007-02-09
the inherent flaws with ASP, besides being created by microsoft is that its platform dependant really (relying on IIS) and therefore I won't touch ASP with a 20 foot pole

go ahead and rewrite your code for PHP and you'll never have a portability issue again

---

