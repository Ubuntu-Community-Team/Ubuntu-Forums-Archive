---
title: "Meta data not working"
date: 2010-10-06
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2010-10-06
Hello,
So, I'm having a but of trouble with my meta-data service and I was wondering if anyone might have a little insight.

I'm using curl as my meta-data service and using a little script in the rc.local file to create and append my authorized_keys file. However the command that connects to my meta-data service isn't working.

I'm using:
curl -m 10 -s [http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key](http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key)  | grep 'ssh-rsa'
[FONT=Verdana]
When I use that command my apache error log returns:
File does not exist: /var/www/latest

When I go to the directory on my CC, all I have is an index.html that says I haven't added anything yet.

Am I missing something? Does anyone else have a better way to pass the rsa data to the instance? 
[/FONT]

---

### Post by Ohm's Lawyer on 2010-10-10
Alright, so meta-data is working. I've downloaded some pre-packaged stuff and it works fine. It looks like my problem is that my instance doesn't boot fully. If I run a euca-get-console-output, it tells me "Running /scripts/init-bottom ..." then "[Done]". That's the end of it, but on the pre-packaged stuff there are about 15 more processes after that. 

The funny part is I can KVM into my image perfectly, I can install everything I want, but once I bundle it....NADA. Partial boot. Which is, at least a good reason, why I can't ssh into my instance.

Any thoughts?

---

