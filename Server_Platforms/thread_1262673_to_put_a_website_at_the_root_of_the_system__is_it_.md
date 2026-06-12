---
title: "to put a website at the root of the system : is it safe?"
date: 2009-09-10
forum: Server Platforms
---

### Post by hugolambert on 2009-09-10
I don't know why to put a website in var/www.
Is it possible to put it directly at the root of the ubuntu server?
Is is secure, and if not, why?
Thank's!
Hugo

---

### Post by terazen on 2009-09-10
How are you copying files from another system to the webserver?  Are you using ftp?

---

### Post by cdenley on 2009-09-10
> **hugolambert said:**
> I don't know why to put a website in var/www.
Is it possible to put it directly at the root of the ubuntu server?
Is is secure, and if not, why?
Thank's!
Hugo

You want to put your files directly in the root directory (/), then make your root directory publicly accessible? This is the worst thing you can do because that would make your entire filesystem accessible to the public, except for filesystem permissions. They would be able to read /etc/passwd, logs, and files in your home directory. If you want to use a directory besides /var/www, that is fine as long as there is nothing within that directory except the files you intend to allow access to.

---

### Post by recentcoin on 2009-09-10
I second C Denly.  Why make your entire server accessible to the planet?  That's just asking to be hacked.

Keep in mind that you have to give your webserver (usually nobody or a similar unpriviledged system account) access to those files.  That means "nobody" can read /etc which is all your configuration stuff....

VERY BAD IDEA....

---

### Post by jondkent on 2009-09-10
> **hugolambert said:**
> I don't know why to put a website in var/www.

I don't understand why you would want to do this?  It is no more complicated to place files into /var/www than /, yet /var/www can be chrooted off and made safer etc etc.

Any reason for the question?

---

### Post by hugolambert on 2009-09-10
because I want a create a virtual file system with a web interface, just like webmin.
Why is var/www/ so protected compared to other folders?
Why not going to etc by doing ../../../ ?

---

### Post by cdenley on 2009-09-10
> **hugolambert said:**
> because I want a create a virtual file system with a web interface, just like webmin.
Why is var/www/ so protected compared to other folders?
Why not going to etc by doing ../../../ ?

Apache does not allow access to parent directories which have not been configured to be accessible. Such a link will not work:
[http://mydomain.com/../../etc/passwd](http://mydomain.com/../../etc/passwd)
However, if you set DocumentRoot to "/" as you seem to be asking about, this would work:
[http://mydomain.com/etc/passwd](http://mydomain.com/etc/passwd)
If you have any scripts which allow unauthenticated users to access arbitrary files outside of /var/www, then that is a vulnerability with your script. You don't have to set DocumentRoot to "/" in order for your scripts to be able to access any file it has permission to read. Giving a server permission to configure your system like webmin does would have some serious security implications. You shouldn't attempt something like this unless you know what you're doing.

---

### Post by hugolambert on 2009-09-13
Ok, I see. Thanks. 
But how does webmin to make all the files readable? How to do something similar with a web interface?

---

### Post by windependence on 2009-09-14
I think you are confused. You are thinking that the files will show as /var/www in your directory listing. If you set /var/www as your root directory, and files you put in the /var/www directory will show as / in your Apache directory listing. It is suicide to do what you are thinking about doing. Traditionally, /var is used for things that will grow or contract, or change frequently such as log files or web sites. This is why Aapche defaults here for some operating systems. This way, if your /var partition fills up, you don't fill your root partition such that you can't even boot.

-Tim

---

### Post by cdenley on 2009-09-14
> **hugolambert said:**
> Ok, I see. Thanks. 
But how does webmin to make all the files readable? How to do something similar with a web interface?

I've never really used webmin, but I don't think it uses apache. I think it is its own web server. It must either run as root or communicates with a slave process which runs as root in order to perform many administrative tasks. Allowing any kind of root access remotely creates a security risk, but that is why webmin requires authentication, and it probably escalates to root privileges as little as possible to minimize the possibility of a root exploit.

The idea of a DocumentRoot may not apply to webmin, but the DocumentRoot only specifies which pages are served by apache, not which files your web application(s) have access to. Just because apache will not serve "/etc/passwd" doesn't mean your web application cannot read it.

---

### Post by hugolambert on 2009-09-14
Ok, I'll go deeper into this.
But do you think that a website with ssl and a login could, with suphp, execute shell scripts and also get access, through a virtual file system, through the server files without any security problem? (in the classic apache directory)
Sorry about these questions, but that's the one I need to solve to launch my project

---

### Post by cdenley on 2009-09-14
[s]I've never used suphp before, but I believe if the PHP script is owned by root, it will execute as root, and will be able to access any file on any mounted filesystem as root, as well as execute commands as root.[/s] You do not need to change DocumentRoot or place scripts in "/" in order to accomplish this, unless suphp has some sort of chroot function I'm not aware of.

[B]CORRECTION:
suphp will not run your scripts as root[/B]
[http://www.debian-administration.org/article/Running_PHP_scripts_as_specific_users_with_suphp](http://www.debian-administration.org/article/Running_PHP_scripts_as_specific_users_with_suphp)
> 
Notes the way the module works is to look at the owner of the script, and then become that user to execute it, **but it will refuse to execute scripts owned by root**. You should instead add a user to own those files.


You are relying on the strength of your password as well as apache being configured correctly to restrict unauthorized access to your script. Is the SSL certificate signed by a trusted certificate authority so you can tell if your site is being spoofed? There is a very unlikely possibility that apache can have a bug which allows unauthorized access to your script. Also unlikely, though it happened once before, is that a vulnerability in openssl can be discovered which makes your SSL key vulnerable to attack.

Assuming it is configured and maintained properly, I would say this is secure. However, "secure" is a relative term. Your system would be more secure without such a configuration. I would say the same about installing webmin, though, which is one of the reasons I never used it.

---

### Post by hugolambert on 2009-09-15
thank's a lot. would be an euphemism to say you're not a rookie... ;)
At this stage I'll start by that and see next how to improve it. At least I don't see any alternative.

---

