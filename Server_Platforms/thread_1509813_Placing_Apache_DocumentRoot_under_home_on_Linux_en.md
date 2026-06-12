---
title: "Placing Apache DocumentRoot under /home on Linux environments"
date: 2010-06-14
forum: Server Platforms
---

### Post by victor.gscardoso on 2010-06-14
I've just installed Netbeans 6.8 under Ubuntu  10.04 as a Drupal local development environment, before I put the sites  live on the web. 
 
Up until now I've had my *Apache  DocumentRoot* located on the */var/www*  folder, but on the *Configuring the  PHP Development Environment the Linux Ubuntu* tutorial page [http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot)  advices to place it under */home*  instead of  */var*.  
What are the reasons for this option?  

[LIST]
[*]Backup strategies? 
Permission access? 
...?
[/LIST]
 
In several Drupal video tutorials that I've seen, the *public_html* folders are indeed on the  */home* or on the *C:*, but I've always associated this  to the MAMP or WAMP stacks design (usually this tutorials run on Mac or  Windows machines) and not to a functional advantage.
_________________
Victor Cardoso

---

### Post by Ryan Dwyer on 2010-06-14
Ease of editing and backup, I guess. If you're the only user who's managing those files you may as well put them in your home directory. Apache has readonly access to them regardless of whether they're in /var or /home (unless you change the permissions).

---

### Post by tgalati4 on 2010-06-14
Well, if you are doing development work, you can have two locations /home/user/www and /var/www.  You can check the internal pages for new stuff that you create and push them to /var/www when you want them to face the public.

This way you have a backup already, and it would get captured whenever you backup /home.  Your public pages would presumably stay up longer since you are only pushing code that you have personally tested locally.

---

### Post by kidpurple on 2010-08-12
I was just about to ask the very same question.  My problem is that when I did follow the guide and put the website in my home directory I get a 403 error when I try to load it.  If I follow the same steps but put it under /var/www it works but then I have a had time editing/adding files.

I guess I'd prefer the home directory, just can't figure out how to make apache2 like that yet.

---

### Post by Ryan Dwyer on 2010-08-12
Check your /var/log/apache2/error.log to see what the cause of the error is.

EDIT: Oh wait, you said it's a 403 (forbidden) error. Apache probably doesn't have read access to your www folder. What are the permissions on it?

---

### Post by kidpurple on 2010-08-12
> **Ryan Dwyer said:**
> Check your /var/log/apache2/error.log to see what the cause of the error is.

EDIT: Oh wait, you said it's a 403 (forbidden) error. Apache probably doesn't have read access to your www folder. What are the permissions on it?

Actually I get the 403 when I try to use a directory inside /home.  when I put it in /var/www it was fine but I had trouble modifying the contents of that directory.

Thanks for the tip, I will check out that log file tonight.

---

