---
title: "Ubuntu Studio 11.04 Log-In Issue"
date: 2011-09-25
forum: Ubuntu Studio
---

### Post by harryrf on 2011-09-25
I am having an issue with logging into my "main" account on Ubuntu Studio 11.04. When I click on my name I get three errors one after another. From first to last they are. 

First:
"Could not update ICEauthority file home/harry/.ICEauthority" 

Second:
"There is a problem with the configuration server. (/usr/lib/libconf-sanity-check-2 exited with status 256)"

Third:
"Nautilus could not create the following required folders: /home/harry/Desktop , /home/harry/.nautilus. Before running Nautilus, please create these folders or set permissions such that Nautilus can create them."

I have tried:

mkdir /home
mkdir /home/harry/Desktop (and /.nautilus)

also I saw on the forums someone suggested using

chown harry:harry: /home/harry/.ICEauthority
chmod 644 /home/harry/.ICEauthority
exit

None of those worked. There was also another approach that I did not write down so I don't remember what the commands were.

Thanks for the help and I hope I didn't post this in the wrong section.

---

### Post by maul9999 on 2011-09-26
> **harryrf said:**
> I am having an issue with logging into my "main" account on Ubuntu Studio 11.04. When I click on my name I get three errors one after another. From first to last they are. 

First:
"Could not update ICEauthority file home/harry/.ICEauthority" 

Second:
"There is a problem with the configuration server. (/usr/lib/libconf-sanity-check-2 exited with status 256)"

Third:
"Nautilus could not create the following required folders: /home/harry/Desktop , /home/harry/.nautilus. Before running Nautilus, please create these folders or set permissions such that Nautilus can create them."

I have tried:

mkdir /home
mkdir /home/harry/Desktop (and /.nautilus)

also I saw on the forums someone suggested using

chown harry:harry: /home/harry/.ICEauthority
chmod 644 /home/harry/.ICEauthority
exit

None of those worked. There was also another approach that I did not write down so I don't remember what the commands were.

Thanks for the help and I hope I didn't post this in the wrong section.

Hmm. you might will want to use Ubuntu Studio DVD to reinstall one of file .ICEauthority.  I'm not sure if i remember.  I'm former owner of desktop with Ubuntu Studio.

---

