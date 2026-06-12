---
title: "Apache 2 www-data permissions"
date: 2007-09-18
forum: Server Platforms
---

### Post by Praemon on 2007-09-18
Hi,

I'm currently battling with getting the www-data permissions correct. All in all, everything works fine, however, a program I run needs to run 'ifconfig' through exec (php). Although most commands work without problem, 'ifconfig' doesnt, and I presume there is a permission problem, however, Im unsure of how to allow this permission.

Any help would be appreciated.

Thanks

Ubuntu 7.04 - Feisty Fawn
MySQL 5.0.38
PHP 5.2.1
Apache 2.0

---

### Post by EmmEff on 2007-09-18
/sbin/ifconfig has permissions 0755 (global execute is the important bit here), so www-data has execution permissions.

Did you try specifying a fully qualified path in the exec() call or perhaps PHP doesn't allow execution of binaries in /sbin?

---

### Post by Praemon on 2007-09-18
Thanks for the quick reply EmmEff. When I changed it to the full path, it worked. Can't believe i didnt think of that, thanks!

---

### Post by mravenca on 2008-06-20
Hello, I have a similar problem.

I need to execute following command:

if($policko=="on") 
{
	exec('/bin/parashell 0x378 255', $result);
}

This should set all bits on parallel port to "1".
I check this by connecting LED to the parallel port.

At first I checked the privilleges - /bin/parashell is set to be executed by anybody.

Maybe it is useful to say that running this as root from command line works.
When I try to run this command as an ordinary user, I get this:

vasek@ubuntu1:~$ parashell 0x378 1
ERROR: Can't gain access to port 378

Thanks for reply

Vasek

---

### Post by mravenca on 2008-06-20
I solved the problem by changing privileges of execution /bin/parashell to be executed as root by 

chmod +s /bin/parashell

Then my control web page started to work properly..

---

