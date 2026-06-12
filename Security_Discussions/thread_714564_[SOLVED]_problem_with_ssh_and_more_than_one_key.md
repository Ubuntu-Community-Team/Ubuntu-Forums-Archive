---
title: "[SOLVED] problem with ssh and more than one key"
date: 2008-03-03
forum: Security Discussions
---

### Post by Biochem on 2008-03-03
Hello to all.

I want to have 2 set of rsa key for ssh authentification. One is encrypted and is used in acounts where I have root priviledge. the second is to have a password less connection for sshfs and some script. 

The encrypted one is the first I created a couples of months ago with sh-keygen, it was created on my desktop and I transfered a copy to my laptop. I was able to connect to my desktop and was ask for the password. 

Later on I installed seahorse to administer my gpg files. Since then whenever I try to connect to a ssh server it ask for my keys password. If there is no key involved I clic cancel to resume the authentification.

During the weekend I created a second set of key, this time using seahorse, still on my desktop, and this one is password less. I transfered the public key to the relevant server and created a ~/.ssh/config file with the following entry

```

Host *.some.host.com
Compression yes
ForwardX11 yes
User RemoteUser
IdentityFile ~/.ssh/id_rsa.somehost

```

Now the first problem which is relatively minor. When I try to connect to a.somehost.com in a terminal there is a gui window that pop up asking me for my password at LocalUser@RemoteUser. I clic cancel and then the appropriate key is used. This doesn't happend when I connect from Ctrl+Alt+1, so I suspect it's seahorse related.

Now the serious problem! I copied the keyset and the config file to my laptop. And I can connect to some.host whitout my password like expected. But I'm not ask for my password whan I connect to my desktop either. Even though the password less key is NOT in my authorized_keys file!! That is obviously not what I whant!

Anybody have an idea on how to solve my problems? I really don't like the idea that a key can connect to my computer even though it's not authorized to do so.

Thanks in advance

---

### Post by Biochem on 2008-03-04
OK my bad,

Somehow the password for the key was saved into seahorse. I deleted it and restarted X it works now. Probably that synaptic touch pad I's not the first time it * me. I'm setting MaxTapTime=0 option right now in xorg.conf.

For the popup asking for a password it was simply a question of removing the "Automatic Loading of secure shell keys" in seahorse preference.

Thank to all of you who pondered on my questions

---

