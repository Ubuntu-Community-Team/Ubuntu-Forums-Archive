---
title: "Is it possible to make apache return with nothing?"
date: 2011-04-11
forum: Server Platforms
---

### Post by compiz addict on 2011-04-11
[SIZE=3]Hi. I'm running a server and Cogeco doesn't want that.

What I want to do is make it so when someone goes to my_domain/ apache will pretend it doesn't exist, but I want subdirectories to work still.

What I tried was denying access to /var/www, but the apache returns with a message for that.
[/SIZE]

---

### Post by SeijiSensei on 2011-04-11
You could create an empty index.html in /var/www like this:

```

sudo cat /dev/null > /var/www/index.html
sudo chown www-data.www-data /var/www/index.html
sudo chmod 0644 /var/www/index.html

```

This will overwrite the default "It Works!" file that comes with Ubuntu.  If you care, you can make a backup of that index.html first before creating the empty one.

/var/www/index.html should have zero bytes after this procedure.

---

### Post by nerdy_kid on 2011-04-11
I would assume they use something a little more complex then just looking at the web page, they probably detect the open port.  I would try perhaps having apache operate on a different port.

---

### Post by compiz addict on 2011-04-11
only problem with the blank index.html idea, is that my server returns a blank HTML file, rather than pretending not to exist.

---

### Post by BkkBonanza on 2011-04-12
What you need is for Apache to drop the request completely when it's not for a certain defined location. Any response by Apache at all will be detected, including a blank file which still gets http headers added. I would suggest trying a rewrite rule that just drops the request.

mod_security may have something for you too.

Unfortunately I've been using nginx for the last couple years and lost my rewrite mojo to give a specific rule that works.

I would recommend nginx as a better solution anyway unless you really need some apache module. In nginx returning a 444 (non-standard) error code is a signal to drop the connection so you can do this,

location = /whatever {
  return 444;
}

Edit: If this isn't for public use then another thing to consider is [port knocking]("http://www.thoughtcrime.org/software/knockknock/") - this keeps the port closed unless a secret knock-knock is done and then it opens (at the iptables level).

---

### Post by SeijiSensei on 2011-04-12
I'm not comfortable with giving advice on how the OP can surreptitiously violate his terms-of-service.

---

### Post by Ryan Dwyer on 2011-04-12
I seriously doubt any solutions posted here will work. Your ISP is most likely blocking or counting the incoming requests on port 80. Whether your homepage or subdirectories return anything is irrelevant.

You could try using a different port, or you could change plans/ISPs to one which allows you to run servers.

---

