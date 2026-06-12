---
title: "How to build private cloud?"
date: 2014-03-24
forum: Server Platforms
---

### Post by Eoiser on 2014-03-24
I want to build a private cloud.
Functionality should be exactly like google drive or dropbox.
This will only have about 10 persons using it.

Every person should have an account each and a personal "space" or folder on the cloud
Every client computer should have a folder which sync up to my server.

Bonus if it was possible to host an interface on a webserver on the same server using my private domain.


What services/software would i need for this?

Ive looked at the Ubuntu openstack with maas, juju and landscape, but i have not found a good explaination how it works.

---

### Post by volkswagner on 2014-03-24
I suggest checking out [OwnCloud]("http://owncloud.org/")

---

### Post by thnewguy on 2014-03-24
Things like OpenStack and Juju are way too much overkill for a simple setup like this with just ten users. What you are looking for is ownCloud (which is available in the repositories). Just run "apt-get install owncloud" on your server and you are good to go. The ownCloud client software, for your ten users, can be installed from the owncloud.org website.

---

### Post by Eoiser on 2014-03-24
But Openstack and juju is pretty much the same thing as owncloud?
I was thinking about doing this educationally as well, so it beeing "Overkill" doesn't really matter. I just want to learn more about servers

---

### Post by volkswagner on 2014-03-24
MAAS is way more than the features you are requiring.

I can't read the [MAAS]("http://maas.ubuntu.com/docs/") docs for you.

How many physical hardware servers do you plan to deploy for your ten users?
If it's only one, MAAS makes little sense.

I thought you were asking for advise on what software to deploy for your solution.

If you want to learn more about MAAS and Landscape, google is your friend.

---

### Post by Habitual on 2014-03-24
> **Eoiser said:**
> But Openstack and juju is pretty much the same thing as owncloud?Not even close.
OwnCloud is *software.* Just marketing hype with the "cloud" label on some decent software using [Cloud Storage]("http://en.wikipedia.org/wiki/Cloud_storage") technology
Openstack and juju are [Infrastructure as a service]("http://en.wikipedia.org/wiki/Infrastructure_as_a_service").

[http://en.wikipedia.org/wiki/Cloud_computing](http://en.wikipedia.org/wiki/Cloud_computing)

---

### Post by Bailey_Allen on 2014-03-24
hey guys,
i want to run a laptop 24/7 running ubuntu server + owncloud server...

the aim here is to be able to access all my files on many machines from my LAN and via the internet.

also after this is done i was hoping i could have multiple users, that could login and only be able to see folders they have access to...
eg if they can read/write in their personal folder, read from a shared folder, and neither on someone else's personal folder, they should only see their own personal folder + the shared folder.

---

### Post by Bailey_Allen on 2014-03-24
i have used freenas on a virtual machine and that was running nicely in my LAN, but users could see folders they aren't meant to be able to see.
the reason this is important is because several family members dont get along and there will be family, friends and maybe friends parents all using this...

i dont want 'jane lowe's folder' being seen by michael for example. (i understand he cant see whats inside but its better if they didnt know the folder existed)

---

### Post by koenn on 2014-03-24
+1 for owncloud

also worth considering  : Pydio  [http://pyd.io/](http://pyd.io/)
it offers the same basic functionality as owncloud but is different in concept, in that it is more "plugable", e.g. it can also be used as an overlay over an existing directory tree to make files (on local disk, on NAS, even in selected CMS, ...) instantly accessible through a browser. The desktop sync client is still beta, though.

---

