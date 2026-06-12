---
title: "[SOLVED] ~user directories"
date: 2005-05-08
forum: Server Platforms
---

### Post by ZiRo on 2005-05-08
i've installed apache, however i am struggling to make a configuration change to it.

I've edited /etc/apache2/apache2.conf but it has not seemed to have changed the root. Am i editing the wrong file?

And also, how would one go about making 10.0.0.5/~ziro deliver my own folder?

Is it possible to manipulate the create user scripts to create directory maps within the users home or elsewhere upon user creation?

Finally, does anyone know of a web based ssh client. Not Java, not executable. My college blocks unknown applications from using any socket and blocks all but port 80.. so i need something that isn't java based that will let me communicate with my ssh.

Oh also, if anyone could give me a run down of the directory's meanings. eg. /etc/
so i can better find what i'm looking for in future that would be great.

Thanks in advance,
ZiRo

-Yes I'm a complete newbie, this is my first proper linux attempt and i'm 12 hours into it :)

---

### Post by JonahRowley on 2005-05-08
[QUOTE=ZiRo]i've installed apache, however i am struggling to make a configuration change to it.

I've edited /etc/apache2/apache2.conf but it has not seemed to have changed the root. Am i editing the wrong file?[/quote]

You must run **sudo /etc/init.d/apache2 restart** after editing that file.  Are you doing this?

> And also, how would one go about making 10.0.0.5/~ziro deliver my own folder?
By default, that URL will go to **~ziro/public_html**, if this is what you want, I think it's in the default configuration.  If not, the lines are there, they must be uncommented.

> Finally, does anyone know of a web based ssh client. Not Java, not executable. My college blocks unknown applications from using any socket and blocks all but port 80.. so i need something that isn't java based that will let me communicate with my ssh.
Not executable?  Not Java?  You options are limited.  There is a signifigant amount of crypto work being done in SSH, you find hacked up versions like you would with telnet.  As for the blocked ports, run a proxy on port 80 (with authentication) that can connect to any of the services on your machine.  Not sure that software you'll need for that though.

---

### Post by ZiRo on 2005-05-08
thanks for your input, and yeah i'm restarting the server. Perhaps it did not restart, but i'm confident it did.

I've just tried it again and i've got this:
>  * Forcing reload of web server  (Apache2)...
apache2: Could not determine the server's fully qualified domain name, using 10.0.0.8 for ServerName
httpd (pid 5962?) not running

It's right, httpd is not running in the process list..

At the moment, apache is pointing 80 at **/vars/www/**, how does /~user point it at **/home/user/public_html **? I don't see the logic.

---

### Post by LordHunter317 on 2005-05-08
> **JonahRowley]You must run **sudo /etc/init.d/apache2 restart** after editing that file.  Are you doing this?[/quote]Actually a reload normally sufficies, unless you change DSOs basically.
 
 You shouldn't put a master document root in /etc/apache2/apache2.conf said:**
> It's right, httpd is not running in the process list..That's because it's actually called apache2, not httpd.  A bug that Debian's never fixed since it's apachectl spitting out that message.

> how does /~user point it at **/home/user/public_html **? I don't see the logic.Because the mod_userdir DSO does this.  Apache lets loadable modules (DSOs) and the system administration graft in points anywhere they want in the webroot.  Using the Alias directive, I can make [http://example.com/foo](http://example.com/foo) point to anywhere I want on the filesystem.

The mod_userdir configuration should be in /etc/apache2/modules-enabled/userdir.conf.  You can look at the documentation for it at httpd.apache.org if you want to change it's configuration.

---

### Post by dargles on 2008-02-21
> **LordHunter317 said:**
> ...The mod_userdir configuration should be in /etc/apache2/modules-enabled/userdir.conf.  You can look at the documentation for it at httpd.apache.org if you want to change it's configuration.

Hi, Folks.
I know this is 2 years on, and we're now on to Apache2, but... I can't find the place to edit to get "localhost/~user/" to work (userdir.conf doesn't exist in the latest version).  Can anyone point me in the right direction, please?

Regards, David

---

### Post by dargles on 2008-02-21
> **dargles said:**
> Hi, Folks.
I can't find the place to edit to get "localhost/~user/" to work (userdir.conf doesn't exist in the latest version).  Can anyone point me in the right direction, please?
Regards, David

OK, I've just answered my own post...

[LIST=1]
[*]Go to /etc/apache2
[*]assume root identity
[*]copy userdir.conf and userdir.load from mods.available to mods.enabled
[*]reboot (or presumably stopping and restarting the apache daemon would do the trick)
[/LIST]

Hope this helps anyone else with the same question.

Regards, David

---

### Post by MJN on 2008-02-21
Just a few comments on 2, 3 and 4.. ;-)
 
2. You should use **sudo** for this
 
3. Don't copy the files - use the Apache tools **a2enmod **(and **a2dismod** to disable) to create symlinks in sites-enabled/
 
4. As you say, no need to reboot either reload (**sudo /etc/init.d/apache2 reload**) or restart (**... restart**) Apache for the changes to take effect.
 
Mathew

---

