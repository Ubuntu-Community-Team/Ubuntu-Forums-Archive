---
title: "Nagios initial installation help"
date: 2009-09-15
forum: Server Platforms
---

### Post by cLos420 on 2009-09-15
Hey guys,

So, I'm following the steps from this site:

[http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

And am stuck on step5. 
Upon running make install-webconf I get the error:
flash 
make: *** No rule to make target 'install-webconf'. Stop.

The directions says install the Nagios web config file in the Apache conf.d directory.
I did a search for the directory and found this:
/etc/php5/apache2/conf.d (files found: pdo.ini)
/etc/apache2/conf.d (files found: charset, security)

I'm assuming that the webconf file should be installed in the /etc/apache2/conf.d folder.

How do I do this?
Thanks guys, I appreciate the help.


[EDIT] I found this but unsure what to do with it:

[https://answers.launchpad.net/ubuntu/+question/77089](https://answers.launchpad.net/ubuntu/+question/77089)
Thanks!

---

### Post by KiLaHuRtZ on 2009-09-15
The Nagios file for Apache is just simply a virtual server file.  I run, and have been, running Nagios for about 5 years now.  That said, I do all my configuration by hand.  It takes a little time, but in my opinion, gives you more control over what is going on.  I would suggest you read and follow the Nagios documentation as it requires extensive configuration to function properly.  It's, by no means, a simple program you can install and have working in 15 minutes.  [http://support.nagios.com/knowledgebase/officialdocs](http://support.nagios.com/knowledgebase/officialdocs)

---

### Post by mbradlcu on 2009-09-15
I have nagios2 setup on a few machines. All installs have been from the repos. This way the apache and nagios user steps are taken care of,, and you can focus on the fun part of configuring it ; )

---

### Post by cLos420 on 2009-09-15
> **mbradlcu said:**
> I have nagios2 setup on a few machines. All installs have been from the repos. This way the apache and nagios user steps are taken care of,, and you can focus on the fun part of configuring it ; )


Thanks guys!
I did not know you could install it from repository!! Made my life a whole lot easier, still wished I could have finished the config manually. I was so close, I'm pressed for time so that will have to be for a later time.

I have a new question, a little dumb :lolflag:, but the documentation on the Nagios site does not provide much info on the following:


I'm setting up the username and passwords on the resource.cfg.

Where and How do I setup the password?

$USER1$=NAGIOSUERNAME 
where does the password go??

Thanks!

---

### Post by mbradlcu on 2009-09-15
I believe it's /etc/nagios2/htpasswd.users I don't remember but it may need the 'htpasswd' program to set it up.

you'll find the line: AuthUserFile /etc/nagios2/htpasswd.users
in the /etc/nagios2/apache2.conf

---

### Post by cLos420 on 2009-09-15
> **mbradlcu said:**
> I believe it's /etc/nagios2/htpasswd.users I don't remember but it may need the 'htpasswd' program to set it up.

you'll find the line: AuthUserFile /etc/nagios2/htpasswd.users
in the /etc/nagios2/apache2.conf

Bummer, I did not find an htpasswd file under /etc/nagios3/htpasswd (notice that I am using version 3 though)
I'll poke around but, am still stuck on this step :S

Thanks again, your time and knowledge are very appreciated.

---

### Post by mbradlcu on 2009-09-15
yea I think the file needs to be created like so
```

htpasswd -c /etc/nagios3/htpasswd.users someusername

```

you'll be prompted to enter a password

you may have to install the package that has the htpasswd proggy


> **cLos420 said:**
> Bummer, I did not find an htpasswd file under /etc/nagios3/htpasswd (notice that I am using version 3 though)
I'll poke around but, am still stuck on this step :S

Thanks again, your time and knowledge are very appreciated.

---

### Post by KiLaHuRtZ on 2009-09-15
$USER1$ is just a built in macro/variable.  You can set this to anything you like.

For example.

```
$USER1$=/path/to/my/plugins
```

You can later refer to it in a config file.

```
$USER1$/check_something -H $HOSTADDRESS$
```

---

### Post by cLos420 on 2009-09-16
> **mbradlcu said:**
> yea I think the file needs to be created like so
```

htpasswd -c /etc/nagios3/htpasswd.users someusername

```you'll be prompted to enter a password

you may have to install the package that has the htpasswd proggy


Awesome! I created the UID/PWD and it worked. Is there a chance to make more than one account? I created various ones, but only the latest one works (I'm assuming running the command everytime overwrites the previous uid/pwd). 

Is this ok in the apache2.confg:

<DirectoryMatch (/usr/share/nagios3/htdocs|/usr/lib/cgi-bin/nagios3)>
    Options FollowSymLinks

    DirectoryIndex index.html

    AllowOverride AuthConfig
    Order Allow,Deny  #IS THIS PART CORRECT?
    Allow From All #WHAT ABOUT THIS?

    AuthName "Nagios Access"   
    AuthType Basic
    AuthUserFile /etc/nagios3/htpasswd.users 
    # nagios 1.x:
    #AuthUserFile /etc/nagios/htpasswd.users
    require valid-user
</DirectoryMatch>

Next up, beefing up security and then time to monitor some WIndows computers.
You guys rock!!:guitar:

---

### Post by mbradlcu on 2009-09-16
I'm not an expert but your apache.conf looks like mine. You can add users with the htpasswd proggy by not recreating the file eg:

```

htpasswd /etc/nagios2/htpasswd.users some_other_user

```

you know the drill from there ; )

I have some quick and dirty notes on how I setup my systems if you'd like to check them out but it seems you're already on your way

---

### Post by wjrhee77 on 2009-09-25
I have the same problem as the original question on this thread.

Im using 8.04 and i cant find nagios on the repository.
apt-get install nagios will not find the package.

Help!:confused:


It seems like 

#apt-get install nagios2

---

