---
title: "Hibernate &amp; Encrypted Partitions"
date: 2014-12-28
forum: Security
---

### Post by Balzy on 2014-12-28
Hello!
I'm running Xubuntu 14.04 LTS and I have a LUKS encrypted hard drive with this structure. I'd like to get Hibernation working as I describe later.

[IMG]http://s24.postimg.org/at3mbswb9/Screenshot_28122014_13_42_04.png[/IMG]

Except for boot partitions,   **/home**,  **/swap**  and **/root** are a ll encrypted and  have a LUKS header.

 
[LIST]
[*]**/root **has a single key which is a password I usually enter at startup 
[*]**/home** and **/swap** have the same key as /root (shouldn't lower security or represents an issue, please tell me if I'm wrong) and a key-file stored on the encrypted /root partition. Same key as /root is set so I can quickly access these partitions from a live without retrieving first key-file from /root. Normally, at startup I enter /root key and other two partitions are unlocked with their key-file on the encrypted /root, so I have to type a single password. 
[/LIST]
 
This is therefore my **/etc/crypttab**:

```

root    UUID=##### SHADOWED UUID #####    none              luks
swap    UUID=##### SHADOWED UUID #####    /root/swapkey     luks,swap
home    UUID=##### SHADOWED UUID #####    /root/homekey     luks

```

So this is my setup. What I'd like to achieve is being able to hibernate my system and bring it back just by entering the **/swap** password, as I do with **/root** password when I boot from a shutdown system.

I've read **/etc/crypttab** reference and searched around the forum but I wasn't able to find anything useful. Hope I've explained clearly my issue.

Thank you for your help,

Stefano

---

### Post by Balzy on 2014-12-28
Found this instructions and solved my issue:
[http://askubuntu.com/a/235992](http://askubuntu.com/a/235992)

I'm not a crypto expert but to me it seems reasonably secure.
If you would like to discuss it here's the topic, otherwise it can be closed and marked as [SOLVED].

Regards

---

