---
title: "XAMMP / Wordpress"
date: 2013-04-24
forum: Server Platforms
---

### Post by TRUBored on 2013-04-24
I'm having a little issue with running a web server on 12.10. I installed xampp which went smoothly and then I installed wordpress which was also without problem. Now when I go to the site on my local network, it works just fine. When I try to access it remotely. I have port 80 forwarded in my router and I have shorewall installed as a firewall with ports 80 and 22 allowed through.

in chrome: it downloads a file named 'download' with nothing in it

in ie8 it just gives a blank page.

Any help or nudges in the right direction would be appreciated

---

### Post by mastablasta on 2013-04-25
you need to set your IP in settings --> general of wordpress (as it's domain). 

if this doesn't work you will need to use other options to "hard code" the IP address.

here is how to hardcode the change in: [http://codex.wordpress.org/Changing_The_Site_URL](http://codex.wordpress.org/Changing_The_Site_URL)

---

### Post by Lars Noodén on 2013-04-25
> **TRUBored said:**
> Any help or nudges in the right direction would be appreciated

You'd also be better off uninstalling the third-party XAMPP and using the packages that come with Ubuntu.  perl, for that matter, is already installed and XAMPP just gives you and extra copy.  As for the other tools, if you use the packages that come with Ubuntu, they will end up in the right directories instead of non-standard locations.  They will also be able to take advantage of automated security updates and notices rather than having to seek out updates and manually install them.  XAMPP may be a leg up for Window users, but it is the hardest most tedious way of doing things in Linux.

You can install Apache, PHP5, and MySQL individually from either the software center, synaptic or apt-get.  There is a meta-package for the whole LAMP stack, too.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

The caret (^) is important.

---

### Post by TRUBored on 2013-04-25
> **Lars Noodén said:**
> You'd also be better off uninstalling the third-party XAMPP and using the packages that come with Ubuntu.  perl, for that matter, is already installed and XAMPP just gives you and extra copy.  As for the other tools, if you use the packages that come with Ubuntu, they will end up in the right directories instead of non-standard locations.  They will also be able to take advantage of automated security updates and notices rather than having to seek out updates and manually install them.  XAMPP may be a leg up for Window users, but it is the hardest most tedious way of doing things in Linux.

You can install Apache, PHP5, and MySQL individually from either the software center, synaptic or apt-get.  There is a meta-package for the whole LAMP stack, too.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

The caret (^) is important.

I'll give it a shot when I get home later, thanks

---

### Post by TRUBored on 2013-04-25
> **TRUBored said:**
> I'll give it a shot when I get home later, thanks


Uninstalled XAMPP
installed the lamp package as you described
went into mysql and created a dbase and a user for wordpress
installed wordpress, everything works ok on my local network even when using my web address

still getting the same results as before.

Would having the box as a VM on an esxi 5 host be an issue here? even if it were why can i access perfectly through my local network? surely that means that port 80 is open on my VM and is accessable. what else can I check?

---

### Post by Lars Noodén on 2013-04-26
You could try opening one extra terminal and watching the web server's access logs or error logs when you try to connect.  That should show you what is going on.  In the open terminal, user [tail -f](http://manpages.ubuntu.com/manpages/raring/en/man1/tail.1posix.html)

```

tail -f /var/log/apache2/access.log

```

or 

```

tail -f /var/log/apache2/error.log

```

---

