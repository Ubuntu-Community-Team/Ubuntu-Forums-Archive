---
title: "Apache2 Config File Setup"
date: 2006-01-20
forum: Server Platforms
---

### Post by spectre_25gt on 2006-01-20
Could anyone give me some details on how Apache2's config files are set up when installed from a Debian / Ubuntu package? I understand how to set up new virtual hosts and modules, but I'd like to know what tells Apache to read from mods-enabled, sites-enabled etc. If possible, I'm hoping to do something similar to break up the config file for JBoss. 

My end goal is to make it easier to write a script that will allow me to add or remove a virtal host quickly and easily. The script would make the necessary modifications to all config files including the zone files for Bind.

---

### Post by adwait on 2006-01-20
/etc/apache2/<differenc config files>

---

### Post by spectre_25gt on 2006-01-21
That much I knew. What I'm really interested in is how they link all the directories full of config files into the main config.

---

### Post by dbee on 2006-01-21
```

Include /etc/apache2/<config-files>

```

---

### Post by spectre_25gt on 2006-01-21
I'm not new to configuring Apache. I understand how includes work. What I was looking for was what the main configuration file was that called the others and how it called them because the debian package differs from a traditional Apache install.

I was able to figure it out, though. Rather than using httpd.conf (which is still there for legacy compatibility) apache2.conf has most of the configuration info. The mods-available and sites-available directories are called with what looks like a regex. e.g. ```
Include /etc/apache2/sites-enabled/[^.#]*
``` I'm not sure exactly what that does, but I'm sure I can find out...

I may take some hell for this, but honestly I'm a little offended. I understand that newbs come to forums all the time and never want to do any research for themselves and that it's annoying when somone posts something like "hey, I can't get this to work, tell me what's wrong". I think my question was fairly well thought out, though, and explained enough to warant more than a quick one-line answer, or maybe a question if something was unclear.

Please don't take this the wrong way. I know that you're volunteering your time to help people through difficulties. I appreciate and respect that, but when I get a reply telling me something that basic I feel a bit worthless.

---

### Post by MJN on 2006-01-22
If I may be so bold as to stick in my 2 pence worth (and probably overpriced at that! ;)) when I read your question you gave the impression with the JBoss reference that you were relatively savvy in this area however your actual question did not align with this. Thus, I was left wondering exactly what your query was so whilst it may have seemed clear to you it certainly wasn't to others (or at least me!).

I'm still not certain what you're asking, and whether or not the simple answers have sufficed? Check out /etc/Apache2/README - I'm sure it's got everything you need.

With regards to the regexp syntax, it's basically matching (and thus including the config contained within) every file that *doesn't* start with a '.' 

Mathew

---

### Post by LordHunter317 on 2006-01-22
[QUOTE=spectre_25gt]I may take some hell for this, but honestly I'm a little offended. I understand that newbs come to forums all the time and never want to do any research for themselves and that it's annoying when somone posts something like "hey, I can't get this to work, tell me what's wrong". I think my question was fairly well thought out, though, and explained enough to warant more than a quick one-line answer, or maybe a question if something was unclear.[/quote]Frankly, if you can't understand how it works from that one-line answer, you are a new when it comes to Apache configuration.  Even if you're unclear on what the regex captures, the intent of the line is self-evident.

---

### Post by spectre_25gt on 2006-01-23
Well, I've never configured Apache on a Debian or Debian based system before. In the past I've had httpd.conf to modify and that was the end of it. One thing that tripped me up was that I overlooked the apache2.conf file (a stupid oversight on my part). So, when httpd.conf had nothing but comments and I didn't find a file that had any sort of link to the mods-enabled and sites-enabled directories I became a bit confused. So, I knew that everything was in /etc/apache2. I just didn't know what the main config file was. I should have read the README. I'm not sure why I didn't. I guess I was thinking that it would probably be the standard readme and not have information that was specific to this package.

In the end I understand pretty well how everything works. apache2.conf being used instead of httpd.conf and how it calls the files in each directory (thanks for the info on the regex btw). Now I've just got to figure out how includes work in JBoss's server.xml and I'll be halfway to solving my problem.

Thanks for the help.

---

