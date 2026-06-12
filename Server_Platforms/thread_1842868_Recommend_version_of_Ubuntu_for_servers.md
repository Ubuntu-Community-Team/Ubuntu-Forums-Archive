---
title: "Recommend version of Ubuntu for servers?"
date: 2011-09-12
forum: Server Platforms
---

### Post by sofakng on 2011-09-12
I know this isn't a straight-forward question, but is it generally recommended to run 10.04 LTS for production servers?

I'm running ESXi with several virtual Ubuntu servers at my house basically as a lab/testing environment so I have a mixture of 10.04, 10.10 and 11.04 servers.

However, I thought about changing everything to 10.04 since it's the current LTS version but I would also like the latest version of Apache, MySQL, etc.

---

### Post by 2F4U on 2011-09-12
Linux administrators of production machines usually take a conservative  view on that topic. If it is a production environment, I would always  recommend to use the LTS version. This makes sense because on a  production server you don't want to upgrade too often. This is why  product such as RHEL or SLES are supported such a long time.  Administrator install and when the OS runs out of support, they throw  away the hardware and to a fresh installation of the new version  parallel to the old machine. This allows them to test everything before  they finally switch.
However, in your home environment, your targets may be totally  different. You may not throw away the hardware but rather upgrade to a  newer version. But that is something only you can decide.

---

### Post by Dangertux on 2011-09-12
Honestly if you are talking about production systems there is absolutely nothing wrong with 10.04 LTS. 

That being said as far as the latest versions of the LAMP stack go, if you're really talking about a production machine you should be compiling from source anyway. Of course after verifying the contents of the source code.

However, for a home or testing server installing from repos is perfectly adequate. Generally the more widely used production servers are either CentOS or RHEL. That being said the elephant in the room is that they are chosen for their support terms. It's also important to note that Ubuntu slightly crippled it's adoption as a production server. Most sysadmins are not all that willing to adopt KVM at this point.

A lot of that is my opinion, and things I've gleaned from my experiences your mileage may vary.

---

### Post by a2j on 2011-09-12
> **2F4U said:**
>  If it is a production environment, I would always  recommend to use the LTS version.

even if it is a server at home.

---

### Post by dudumomo on 2011-09-12
It's even more recommended as some more recent versions will brings you more problem to set up your application with.
I'm talking about the new python version for example.

LTS is supported for 5 Y for servers...Just go with it, there is nothing you can't do with this version.

---

### Post by cj13579 on 2011-09-13
> **a2j said:**
> even if it is a server at home.

+1

---

### Post by jchung on 2011-09-13
> **cj13579 said:**
> +1

+1

---

