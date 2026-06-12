---
title: "PHP 5.2 on Dapper"
date: 2007-06-28
forum: Server Platforms
---

### Post by Bruut on 2007-06-28
Hi

A simple question: I've got a webserver running Ubuntu Dapper. Because of some features, I need PHP 5.2 on it. However, the repositories only support until 5.1.3. 

What's the easiest way to install php 5.2 on dapper?

Thanks

---

### Post by az on 2007-06-28
Dist-upgrade to Edgy and then to Feisty.

---

### Post by Bruut on 2007-06-28
One extra condition, it must be a safe solution. I actually don't trust upgrading the distro, especially for this server, however I don't have experience with upgrading . I don't want to happen that the server needs te be reinstalled.

Any other solutions? Or is it fairly safe to upgrade?

---

### Post by marianom on 2007-06-28
Compile php yourself. That would be the best option I can think of.
What extensions/modules are you using or you need to use?

---

### Post by Steve3 on 2007-06-28
I'm in the same position- have 6.06LTS server installed and running, but want/need to get to the latest PHP.  I'm not opposed to compiling it, but don't want to omit an option I'm already using.

Problem is that PHP on the 6.06 server install has the confgure parameters suppressed in a phpinfo statement, so how do I know what I already have, so I can compile a fresher version and not leave anything out?

---

### Post by Bruut on 2007-06-28
> **marianom said:**
> Compile php yourself. That would be the best option I can think of.
What extensions/modules are you using or you need to use?

I need SimpleXML. That's the biggest issue. Hm, can't I just compile that extension, and let it work with PHP 5.1.13, or is it better to just fully compile PHP5.2?

---

### Post by az on 2007-06-28
Dist-upgrading is the only option that will preserve the current path for security updates.  You don't want to have to manage a large chunk of your server's infrastructure on your own.

It's the only option that leaves you with a supported platform.

I can tell you from experience that dist-upgrading a Dapper server to Edgy and then to Feisty works very well.

---

### Post by Steve3 on 2007-06-28
> **az said:**
> Dist-upgrading is the only option that will preserve the current path for security updates.  You don't want to have to manage a large chunk of your server's infrastructure on your own.

It's the only option that leaves you with a supported platform.

I can tell you from experience that dist-upgrading a Dapper server to Edgy and then to Feisty works very well.



Therefore, compiling a new php on Dapper turns it into a non-supported platform?  

And since I want/need php 5.2.3, I'm required to dist-upgrade Dapper -> Edgy -> Fiesty?

---

### Post by az on 2007-06-28
> **Steve3 said:**
> Therefore, compiling a new php on Dapper turns it into a non-supported platform?  

Well, you can do what you want.  But, by removing all the PHP packages and compiling it from source, you will have to keep in touch with the php security mailing lists and recompile it every time there is a new vulnerability reported for the version of PHP you are running.  The package manager will not do that for you any more.


> **Steve3 said:**
> 
And since I want/need php 5.2.3, I'm required to dist-upgrade Dapper -> Edgy -> Fiesty?

*Required* is a strong word. I think that is the easiest and safest route.

---

### Post by Steve3 on 2007-06-28
But the package manager isn't doing that for me anyway.  On a Dapper system, it doesn't upgrade past 5.1.3, which is over a year old.   Unless I'm doing something wrong, t's effectively dead for php upgrades on Dapper.

I just did a dist-upgrade from Dapper -> Edgy -> Fiesty, and ended up at 5.2.1 (as I recall, I'm away from the server now).  Better, but still 2 releases out of date.

I'd still like the whole ./configure that the source is built on to compile mine manually.

---

### Post by marianom on 2007-06-29
Somebody mentioned that the phpinfo doesn't come with that info in Ubuntu's package (it's incredible, really). With the phpinfo or with the php.ini you should have all the extensions that the php need and then start working with the compilation part.

If you can find that info and post it here, I can try to help you with it. I have my own php 5.2 compiled from source and -in my experience- it's not that hard.

---

### Post by marianom on 2007-07-02
Hey guys, I just read [this blog's entry]("http://blogs.oracle.com/opal/2007/07/02#a144") and I remembered your problem.
This part is important: "*The intent of this "project" is to make a relatively current version of PHP available for testing*". Although it's an oracle site I see losts of php's modules (even mysql and postgresql!!). Take a look [here]("http://oss.oracle.com/projects/php/files/").

Ok.. ok: I know they are rpms but you could use [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto") to convert them to .deb
If you really really need them, you don't want to compile from source and your required extension is there, you should give them a try.

---

### Post by Steve3 on 2007-07-09
That looked like I good idea, so I tried it out.  I must not have done something right, as my php still shows as 5.2.1, not 5.2.3 as the package was.
The conversion went fine, and the installing via mkpg looks like it's OK.  Using dpkg -c, I see that the largest file in the .deb file is

-rwxr-xr-x root/root  10454628 2007-06-14 01:20 ./usr/lib/httpd/modules/libphp5.so

And when I check my /usr/lib/httpd/modules/libphp5.so, it matches.

So I'd think that after restarting apache2 (via /etc/init.d/apache2 restart ), I'd see a new php version listed in my phpinfo.php page, but it's not.

I must still be missing something.

---

### Post by marianom on 2007-07-09
One thing that can be happening (just a wild guess maybe) is that there's a parameter in the apache' s conf file pointing to the previous location (remember that .deb files were packaged with ubuntu's directory structure in mind and the oracle's are based on Red Hat's). I cannot recall where's the apache's conf file when you download it from the repos (when you do it from source, it is httpd.conf). You can check the Synaptic's entry for Apache and check all files installed or you can check the phpinfo entry to see where is the conf. file and verify it.
Let us know.

---

### Post by Steve3 on 2007-07-10
I think you're right about that.  Seems by default, libphp5.so is at

/usr/lib/apache2/modules/libphp5.so

While the alien-converted installer puts it in

/usr/lib/httpd/modules/libphp5.so

So, I backed up the source libphp5.so, copied in the new one, and set the permissions to match.  Restarting apache2 got me:> 
* Forcing reload of web server (apache2)...                                                                            apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: libssl.so.4: cannot open shared object file: No such file or directory 

So /etc/apache2/apache2.conf says to load from the mods-enabled directory.  That contains at php5.load file, which simply says>  LoadModule php5_module /usr/lib/apache2/modules/libphp5.so That's the new libphp5.so  It contains a reference to libssl.so.4, which isn't where it's expected to be. And it's not quite clear to me where it expects it to be.

The overall feeling I'm getting is that I'm not starting down a sustainable path here.

---

### Post by marianom on 2007-07-10
You should modify the apache's conf file to point to the new php 5.2.3 .so, not moving the 5.2.3 library to the 5.2.1 folder (at least, that's what I understand you did). Those libraries have dependencies that cannot be satisfied between different versions. You should update the apache's conf file as if the 5.2.1 does not exist and the new 5.2.3 folder's is the only one you have.

---

