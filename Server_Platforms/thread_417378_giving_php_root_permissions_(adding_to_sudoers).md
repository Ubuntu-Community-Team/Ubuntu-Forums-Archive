---
title: "giving php root permissions (adding to sudoers)"
date: 2007-04-21
forum: Server Platforms
---

### Post by itsalmostreal on 2007-04-21
i've been experimenting with the filesystem functions in php lately, and decided i want to full root access to the user www-data so my scripts can run on anything, no matter the permissions. i successfully changed my sudoers file twice, trying two different configurations to see if it would work.

Heres how i configured it the first time (note that i just cut and pasted the user privilege specification):

# User privilege specification
root     ALL=(ALL) ALL
www-data ALL=(ALL) NOPASSWD:ALL

then i tried to run a simple mkdir in a php script, and got: 
Warning: mkdir() [function.mkdir]: Permission denied

after more searching on the net, i found another suggestion and tried it:

# User privilege specification
root     ALL=(ALL) ALL
www-data ALL= NOPASSWD:ALL

can anybody help me out? i rebooted both times to see if i had to for the changes to take effect, but realize thats not the case considering i've messed this file up before and immediately not been able to sudo anything.

thanks!

---

### Post by jtc on 2007-04-21
Have you considered suPHP?

---

### Post by Frosty Cold Drink on 2007-04-21
Adding a user account to sudoers as all/all doesn't mean the user has root privleges. It means the user account can run a processess with those privelges.

PHP as an apache module will run as whatever apache is running as. If you waht to fudge its privelges without doing that to all of apache, you'll need to use suphp or CGI.

---

### Post by gaten on 2007-04-21
>  i want to full root access to the user www-data so my scripts can run on anything, no matter the permission

This is quite possibly the worst idea I have heard in a long time. Do **not** do this if you are running a web server that is accessible from the outside world. The very reason apache child processes run as the www-data user is to **prevent** something like this from happening. You are just asking to get owned. 

I don't know what suPHP is, but maybe it's a good solution, because what you are suggesting is **not** a good idea.

---

### Post by hollymcr on 2008-01-17
> **itsalmostreal said:**
> : Permission denied


In case anyone find this for future use, the solution is probably in how you are running the mkdir command.

If you use:
    exec("sudo mkdir $dirname");

.. you'll probably be OK. You've configured sudo to allow the www-data user to use it to run certain commands as different users (such as root), but if you just use PHP's mkdir function you're not telling PHP to use sudo, so it won't work.

Whether any of this is wise is another matter, but I think if you need to allow the web user to run some system commands then at least you can tie this down using sudoers even to the extent of only allowing certain commands to be run with certain parameters, which I think is pretty safe if done wisely and carefully.

---

