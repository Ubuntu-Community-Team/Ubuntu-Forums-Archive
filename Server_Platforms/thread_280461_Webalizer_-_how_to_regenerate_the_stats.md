---
title: "Webalizer - how to regenerate the stats?"
date: 2006-10-19
forum: Server Platforms
---

### Post by stiankarlsen on 2006-10-19
Okay, so I've been googling around for a bit, but I haven't come up with any answers, so here's my problem.

I have installed webalizer (it came with the XAMPP package) and it seems to work fine, the first time I opened it (two days ago), it generated accurate statistics for my website, the problem is that when I open it again, it won't update or regenerate the statistics, its displays stats for oct, and says "Generated 17-Oct-2006 22:43 CEST". How do i make it generate/update the stats again?

Thanks, Stian Karlsen.

---

### Post by mazirian on 2006-10-19
It doesn't generate the output on viewing.  You have to run webalizer to generate the output.  It's man page is quite helpful, as are the annotated config files in the package's documentation.  You'll probably want to set up a cron job to run it.

---

### Post by bunnynuts on 2006-10-19
From the Command Line enter the following command:

```
webalizer
```

And you shall have updated stats.

---

### Post by stiankarlsen on 2006-10-19
Sorry guys, forgot to mention that I already tried that, but it just gives me.

> webalizer: command not found

Could it be because I installed it through XAMPP?


Okay, so i looked around my system, it turns out that when webalizer was installed through XAMPP, ubuntu didnt recognize it, and so I installed it thorugh apt-get install webalizer, and its been placed in /var/www/...

problem is that XAMPP is placed in /opt/Lampp/htdocs/...

anyway i can have webalizer installed there instead? cause now it doesnt work.

> Webalizer V2.01-10 (Linux 2.6.15-27-386) locale: en_AU.UTF-8
Error: Can't open log file /var/log/apache/access.log.1


---

### Post by bunnynuts on 2006-10-19
I believe that is the error message you receive if you are not running it as root...thus try ```
sudo webalizer
```or while in the command line make yourself root and run ```
webalizer
```

---

### Post by mazirian on 2006-10-19
command not found means it's not in your $PATH, not necessarily that you must be su to run it.  Just use the whole path to the webalizer to run it or make an adjustment to your $PATH.  You should only need privileges to run webalizer if it is writing it's output to a directory you don't have write access to.  IN any event, webalizer was installed the first time, it's just that apt didn't configure it for you.  Whemn you installed it the again via apt, apt ran seom post install scripts that probably assume you maintain a website in /var/www.  That obviously doesn't suit your needs.  So we're back to my first post.  Please read the man page for this app, it really will give you everything you need to know.

---

### Post by stiankarlsen on 2006-10-19
> **mazirian said:**
> command not found means it's not in your $PATH, not necessarily that you must be su to run it.  Just use the whole path to the webalizer to run it or make an adjustment to your $PATH.  You should only need privileges to run webalizer if it is writing it's output to a directory you don't have write access to.  IN any event, webalizer was installed the first time, it's just that apt didn't configure it for you.  Whemn you installed it the again via apt, apt ran seom post install scripts that probably assume you maintain a website in /var/www.  That obviously doesn't suit your needs.  So we're back to my first post.  Please read the man page for this app, it really will give you everything you need to know.


how do I adjust my $PATH?

(thanks guys, for such quick response)


EDIT:

think i figured it out, there was some php file in the XAMPP dir that was configured to update webalizer every two days, explains the problem.

thanks a lot to all answers anyways, im out

Stian Karlsen.

---

