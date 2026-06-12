---
title: "pointing .com .org etc to one set of files"
date: 2009-09-21
forum: Server Platforms
---

### Post by krraleigh on 2009-09-21
I know this question has been asked a number of times and I am sure there a multitude of ways to do it, but how do I setup my apache2.2 vhosts so that I don't have to configure a separate vhosts file for each change in domain extension
such as domain.com, domain.org, domain.name etc...
 
I used a mod-vhost-alias rule so that I could parse the VirtualDocumentRoot so that I could run as many subdomains as I wanted to without hassel, but I still need to be able to catch when the domain is a com, org etc..
 
The vhost-alias rule that I have for setting up a multitude of subdomains is:
> # get the server name from the Host: header
UseCanonicalName Off
# this log format can be split per-virtual-host based on the first field
LogFormat "%V %h %l %u %t \"%r\" %s %b" vcommon
#CustomLog logs/access_log vcommon
# include the server name in the filenames used to satisfy requests
VirtualDocumentRoot /home/user/public_html/domanName/subdomains/%1/public
ServerAdmin [EMAIL="admin@stuff.net"]admin@stuff.net[/EMAIL]
ServerName [www.domain.com]("http://www.domain.com")
ServerAlias *.domain.com
<Directory />

 
any insight would be appreciated
thank you
kevin

---

### Post by openfly on 2009-09-21
Honestly I'd never do this.

I'd setup a vhosts.d

have a XXXXX.com.conf and an XXXXX.org.conf 

When making changes I'd change one, copy it to the next then run a 
:%s/.com/.org/g in vi.

Call it a day.

Reason being, it's easier to bulk manage vhosts when they all have their own individual .conf file in a vhosts.d.

better for automation and larger scripting.

That's just my opinion though.

---

### Post by krraleigh on 2009-09-21
Same problem slightly different
 
I type in [http://your-special-event.com](http://your-special-event.com) and it takes me to the apache2 home pages stating that it works.
 
I type in [http://bethel.your-special-event.com](http://bethel.your-special-event.com) and my wild cards are working great
 
I type in [http://www.your-special-event.com](http://www.your-special-event.com) and my page works normally
 
To get the wild cards to work correctly I modified my subdomain vhosts file as follows:
 
> <VirtualHost *:80>
# get the server name from the Host: header
UseCanonicalName Off
 
# this log format can be split per-virtual-host based on the first field
LogFormat "%V %h %l %u %t \"%r\" %s %b" vcommon

# include the server name in the filenames used to satisfy requests
VirtualDocumentRoot /home/kevin/public_html/yourspecialevent/subdomains/%1/public
        ServerAdmin [EMAIL="admin@domain.net"]admin@domain.net[/EMAIL]
        ServerName [www.your-special-event.com]("http://www.your-special-event.com")
        ServerAlias *.your-special-event.com

 
So how do I get [http://your-special-event.com](http://your-special-event.com) to point to [http://www.your-special-event.com](http://www.your-special-event.com)
 
 
thanx
Kevin:guitar:

---

### Post by krraleigh on 2009-09-21
> **openfly said:**
> Honestly I'd never do this.
 
I'd setup a vhosts.d
 
have a XXXXX.com.conf and an XXXXX.org.conf 
 
When making changes I'd change one, copy it to the next then run a 
:%s/.com/.org/g in vi.
 
Call it a day.
 
Reason being, it's easier to bulk manage vhosts when they all have their own individual .conf file in a vhosts.d.
 
better for automation and larger scripting.
 
That's just my opinion though.
 
I don't have a lot of experience with Vi
what is this doing exactly: 
> :%s/.com/.org/g in vi.
 
Also your saying it would be easier to manage one domain.conf vhost file for each address when they all point to the same set of files?
 
Kevin

---

### Post by i.r.id10t on 2009-09-21
Consider setting up ISPConfig and just using co-domains after creating the one site...

Works well, does mail, dns, web, sql, etc.  Only "down" is that you start from bare hardware for best effects... no real way to bring in everything already there, other than by recreating and then copying files...

---

### Post by krraleigh on 2009-09-21
would take care of the problem I have when I type in domain.com instead of [www.domain.com]("http://www.domain.com") taking me to the default apache page?
 
Rather new to all this...with that is there a decent support community that can help me get my feet wet. Or will I have to go it alone?
 
KEvin

---

### Post by tr333 on 2009-09-21
> **krraleigh said:**
> I don't have a lot of experience with Vi
what is this doing exactly: 
:%s/.com/.org/g in vi. 


That's just a vi command for search+replace to replace all instances of '.com' on a line with '.org'.

---

### Post by krraleigh on 2009-09-21
So in essense this :%s/.com/.org/g in vi.

 
excuse new guy here
 
%s = any string
 
/.com/.org is switch
/g globally look into the file and replace .com with .org
 
can I do this in nano?
 
Kevin

---

### Post by krraleigh on 2009-09-21
answered my own question nano is easy
 
Can anyone advise on why my [http:your-special-event.com ]("http://your-special-event.com") goes straight to the default apache home page?
 
I fixed it temporarily by modifying the vhosts file.
What I did was change ServerName from:
[www.your-special-event.com]("http://www.your-special-event.com")
 
to 
your-special-event.com in the vhosts file
 
now when they type in your-special-event.com they get a 404 which is not great but better than the behavior I had
 
insight appreciated
Kevin

---

### Post by tr333 on 2009-09-21
> **krraleigh said:**
> So in essense this :%s/.com/.org/g in vi.

 
excuse new guy here
 
%s = any string
 
/.com/.org is switch
/g globally look into the file and replace .com with .org
 
can I do this in nano?
 
Kevin

":s" is the command to search and replace
"%" in front of the 's' says to do it over all lines (not just a selection of lines)
/g replaces all occurrences on a line.  Without it, only the first occurrence on each line is replaced.

---

