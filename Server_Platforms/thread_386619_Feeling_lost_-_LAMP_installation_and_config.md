---
title: "Feeling lost - LAMP installation and config"
date: 2007-03-17
forum: Server Platforms
---

### Post by Oceanwatcher on 2007-03-17
This is not a request for a HOWTO. I have been over a few of those already.

I initially posted this in the newbie forum, but was recommended to continue this thread in this forum. So here is the initial post.

The initial thread is at [http://ubuntuforums.org/showthread.php?t=386573](http://ubuntuforums.org/showthread.php?t=386573) and I will post a link to this thread there so it does not run both places.

First of all - I have been hacking various linux distros and freebsd before. But this is my first attempt at Ubuntu.

I really like the idea that everything should be locked down from the start to make installations secure. Kudos to the dev team for this!!

Here is my problem:

I am installing Ubuntu 6.10 server under WMWare 1.02. That part is easy enough.

During the install I am choosing LAMP. But when I try to point a browser to the server, there is nothing to connect to.

I tested ping to the IP. It answers. Tested ping to the server name. It answers and resolves. So the IP is correct, the DNS is set up correct (not done by me - I got the IP and name for the server and I am sure the IT dept know what they do ).

I checked if there was any apache or apache2 under /etc and found nothing. So I do not think that LAMP was installed at all... Then what is the point of having to choose LAMP? I chose Ubuntu because it was supposed to be easy re: installation of LAMP and secure. So far I have verified the secure part. Can anyone help me so I do not loose to much hair scratching my head over this?

Regards,

Oceanwatcher

The big question here is why the LAMP option did not install AMP?

---

### Post by Nikron on 2007-03-17
Well, this happened to me when I installed Ubuntu server too.  It happened because I didn't press the spacebar on the LAMP Option.  Hitting enter on it installs nothing...

---

### Post by Oceanwatcher on 2007-03-17
You are so right! Thank you! This is the only place during the installation you have to use space. Am I totally out of it today, or is this a FAQ? Maybe it should be a sticky...

Dumped the former installation and did a new one. Now it is there. I love WMWare :-)

So now I have to figure out the configuration of the different packages. Time to get back to those HOWTO's.

I think I will start by installing webmin. Really wish it was part of the repository. Why isn't it?

---

### Post by Nikron on 2007-03-17
> **Oceanwatcher said:**
> You are so right! Thank you! This is the only place during the installation you have to use space. Am I totally out of it today, or is this a FAQ? Maybe it should be a sticky...

Dumped the former installation and did a new one. Now it is there. I love WMWare :-)

So now I have to figure out the configuration of the different packages. Time to get back to those HOWTO's.

I think I will start by installing webmin. Really wish it was part of the repository. Why isn't it?

Because it reported security flaws and is no longer regularly developed.

---

