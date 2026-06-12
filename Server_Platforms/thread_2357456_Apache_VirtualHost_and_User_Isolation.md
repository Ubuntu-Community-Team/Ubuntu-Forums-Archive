---
title: "Apache VirtualHost and User Isolation"
date: 2017-04-02
forum: Server Platforms
---

### Post by wolfgentleman on 2017-04-02
What I'm looking for is like what webhosts use. When a user logs into SSH or FTP it should show the VirtualHost's root as /. I also want Apache to chroot into this directory, however, so that PHP, CGI, Python, etc. cannot jump out of the directory. I also want Apache to use the user for the VirtualHost instead of www-data to avoid annoying permission problems.

---

### Post by SeijiSensei on 2017-04-02
For the last item, add the user to the www-data group.  Then if the website directory has group-writable permissions, the user can write there, too.

SSH has the option to use chroot.  Do a Google search for details.

Applications spawned by Apache like PHP have the same limited permissions as the server.  They can't "jump" into other directories and do any damage.  Trying to run all of that in chrooted environments would take a while to set up, since those applications use a lot of system libraries which would need to be replicated in the chroot.  I'm also doubtful you could do this without running multiple Apache instances listening on separate ports.  Then all the URLs would need to have server:port specifications which is really difficult if you're trying to advertise those sites to the public.

I have all my websites in directories under /home/username/ with matching DocumentRoot directives.  I actually use the reverse arrangement from my first suggestion.  All the website directories have user:user as owner:group, but when I need to let Apache write into one of those directories, I add www-data to the user's group rather than vice-versa.

---

### Post by wolfgentleman on 2017-04-02
> **SeijiSensei said:**
> For the last item, add the user to the www-data group.  Then if the website directory has group-writable permissions, the user can write there, too.
I've done that in the past, making www-data as the primary group for the user. It just feels sloppy. And not everything creates files with proper permissions.

> **SeijiSensei said:**
> SSH has the option to use chroot.  Do a Google search for details.
Last time I tried using SSH's built-in chroot, things broke soooo bad.

> **SeijiSensei said:**
> Applications spawned by Apache like PHP have the same limited permissions as the server.  They can't "jump" into other directories and do any damage.
I know, but should someone discover a way to escalate to root from a script, what better way to make it useless than to isolate it.

  > **SeijiSensei said:**
> Trying to run all of that in chrooted environments would take a while to set up, since those applications use a lot of system libraries which would need to be replicated in the chroot. 
I understand this. I'm a patient person. It shouldn't be too hard to design a recursive script that adds a program and all dependencies, which would significantly reduce the labor involved. 

> **SeijiSensei said:**
> I'm also doubtful you could do this without running multiple Apache instances listening on separate ports.  Then all the URLs would need to have server:port specifications which is really difficult if you're trying to advertise those sites to the public.
I think you're onto something. If there's a "master server" that runs internal redirects to the proper port... I could run the Apache servers IN the chroot. If I recall correctly there is a way to run as a specific user in Apache config. That would work...

I cannot test anything right now, so this is all theory and speculation.

---

### Post by SeijiSensei on 2017-04-02
> **wolfgentleman said:**
> I've done that in the past, making www-data as the primary group for the user. It just feels sloppy. And not everything creates files with proper permissions.

I don't know what you mean by "everything."  Anything spawned by Apache like PHP or cgi scripts will run as the www-data user and have those permissions.  

> I know, but should someone discover a way to escalate to root from a script, what better way to make it useless than to isolate it.
And how are they going to do that exactly?  I've run Apache websites for years.  No one has ever done that on a machine I manage.  That's why Apache is designed the way it is.

> I think you're onto something. If there's a "master server" that runs internal redirects to the proper port... I could run the Apache servers IN the chroot. If I recall correctly there is a way to run as a specific user in Apache config. 
Another possibility is to run a master Apache server listening on port 80 in proxy mode.  Then have the individual chrooted servers listening on 127.0.0.1 with unique ports.  The proxy would then pass connections to the other servers.

---

### Post by wolfgentleman on 2017-04-03
> **SeijiSensei said:**
> I don't know what you mean by "everything."  Anything spawned by Apache like PHP or cgi scripts will run as the www-data user and have those permissions.  
I work from so many different clients it's not funny. Some of them spawn new files with no group permission or read-only group permission. Plus files spawned from Apache subprocesses would have a different owner. I remember when I did that I had to set up a cronjob to set ownership and permissions to prevent breakage. It broke less than the alternative though. 

> **SeijiSensei said:**
> And how are they going to do that exactly?  I've run Apache websites for years.  No one has ever done that on a machine I manage.  That's why Apache is designed the way it is.
That's like saying the white house never got hit by a missile, so it doesn't need antimissile defense systems. It's called preventative measures. Just because it hasn't, doesn't mean it can't. 

> **SeijiSensei said:**
> Another possibility is to run a master Apache server listening on port 80 in proxy mode.  Then have the individual chrooted servers listening on 127.0.0.1 with unique ports.  The proxy would then pass connections to the other servers.
By internal redirect, I meant proxy. Sorry about the miscommunication, but you basically described what I had in mind. In the chroot I can set the proper configs to run under the user I choose. It may require a module, but I recall somewhere a config option to specify the user and group the entire server at least.

I won't be able to test this for a couple days, but I will test it as soon as I get a chance and report back. Maybe even write a tutorial if I have the time.

---

### Post by SeijiSensei on 2017-04-03
> **wolfgentleman said:**
> That's like saying the white house never got hit by a missile, so it doesn't need antimissile defense systems. It's called preventative measures. Just because it hasn't, doesn't mean it can't.
There's a lot more to be gained attacking the White House than my webserver.  I have no idea whether that is true for you.  I don't worry about having my server attacked nearly as much as some people.  Maybe I'm just a sunny optimist, but maybe it's based on experience.

It's not that people don't try.  I see break-in attempts in my logs all the time.  I have a good firewall and write fairly secure code.  I actually see more attempts to connect to my POP and IMAP servers than I do attempts against Apache.

But then I'd never let unaffiliated people upload stuff to my servers.  People who want to do that can go to a hosting service and pay a few bucks a month.  Those kinds of customers aren't worth my while.  The only applications running on my servers are ones I've written for clients.

---

### Post by wolfgentleman on 2017-04-03
> **SeijiSensei said:**
> There's a lot more to be gained attacking the White House than my webserver.  I have no idea whether that is true for you.  I don't worry about having my server attacked nearly as much as some people.  Maybe I'm just a sunny optimist, but maybe it's based on experience.

It's not that people don't try.  I see break-in attempts in my logs all the time.  I have a good firewall and write fairly secure code.  I actually see more attempts to connect to my POP and IMAP servers than I do attempts against Apache.

But then I'd never let unaffiliated people upload stuff to my servers.  People who want to do that can go to a hosting service and pay a few bucks a month.  Those kinds of customers aren't worth my while.  The only applications running on my servers are ones I've written for clients.

This [s]may[/s] is definitely true, but it's still best to be prepared. :razz:

---

### Post by wolfgentleman on 2017-05-14
So I finally got around to doing this. I'm running into a problem: Apache from inside the jail is seeming to take over the Apache from outside the jail. I think it may be because of the bind mount for /proc. Tomorrow, I am going to uninstall the master Apache server and install an nginx server in it's place. That should solve that. If not, I did something wrong.

My current system uses debootstrap to install a whole separate copy of Ubuntu Xenial. This makes it bigger, but simpler to work with.

---

