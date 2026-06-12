---
title: "ftp - advisability in creating simlinks"
date: 2009-09-26
forum: Server Platforms
---

### Post by krraleigh on 2009-09-26
I have a tree that looks something like this in my var/www directory.
 
/var/www/public_html/myDomain/subdomains/name_of_subdomain/public/
 
I use adduser to create new user accounts so that I can add documents to the folder via filezilla ftp. That works great, but now I need to get the files from the user folder
to the www/../../public folder. I was thinking that I needed to use simlinks to make this
work correctly, but I was wondering if I am making to much work for myself. Is there a better way?
 
Keeping in mind that I will have about 125 subdomains that load files to the server, I was wondering if there was a way to create an automated short cut so I wouldn't have to do manual simlinks for every new user. I ran across a wiki that showed me how to automate the reading of the subdomain name so that I only had to create one vhosts file for all of my subdomains. Would this idea take me where I want to go?
 
Also I was thinking that I wanted to create a public folder in the user directory and make that the default folder opened when the user logs in via ftp. How would I go about doing that? Are there any links available?
 
:guitar:
thank you
Kevin

---

### Post by Vegan on 2009-09-26
You could mechanize the links with a shell script and call it via cron or even from a web page via PHP

---

### Post by krraleigh on 2009-09-27
> **Vegan said:**
> You could mechanize the links with a shell script and call it via cron or even from a web page via PHP
 
You'll have to forgive my ignorence but I am not at all sure what your talking about.
Could you possibly clarify to this newbie, and possibly give me a link to an example of what your refering to?
 
I definately like the idea of calling it from php or shell, which sounds really cool, but again I haven't quite got this far yet.
 
insight appreciated
thank you
Kevin:guitar:

---

