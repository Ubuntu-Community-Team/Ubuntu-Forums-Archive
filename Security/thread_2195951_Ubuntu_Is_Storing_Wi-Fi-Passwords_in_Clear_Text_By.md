---
title: "Ubuntu Is Storing Wi-Fi-Passwords in Clear Text By Default"
date: 2013-12-27
forum: Security
---

### Post by miguelpires on 2013-12-27
Hi,
Today I came across this:

[http://news.softpedia.com/news/Ubuntu-Is-Storing-Wi-Fi-Passwords-in-Clear-Text-By-Default-412056.shtml](http://news.softpedia.com/news/Ubuntu-Is-Storing-Wi-Fi-Passwords-in-Clear-Text-By-Default-412056.shtml)

Anyone have an Idea how to change this beavior and still let the other users to acces the pass?
Regards
Miguel

---

### Post by ian-weisser on 2013-12-27
There's a lot of tempest-in-a-teacup sensationalism in that link. 

The user is providing conflicting goals. Either the user wants the wireless password encrypted and unavailable from other users (uncheck the "share with other users" box), or the user wants the password open and available for all users (the default, box checked).

> **miguelpires said:**
> Anyone have an Idea how to change this behavior and still let the other users to acces the pass?

Not really. The purpose of encrypting your home directory is to *prevent* other users from accessing your data, including unshared wireless passwords. Letting other users access data encrypted by your key seems like a poor choice.

Perhaps you mean "shared wireless passwords also should be encrypted separately." Rather like what PAM does for your login. And that's possible, if someone wants to write it. But have you looked in /etc/NetworkManager/system-connections/ ? You must be root to read it. Anyone with permission to view those plain-text passwords *already* has permission to become any user capable of decrypting.

It's easy enough to to usability testing to find out which behavior most  users expect to be the default. People come in all varieties - look at  all the threads here of people who encrypted...but then expected  automated tools like backup jobs and file sync daemons to have access to  their encrypted data. The majority expectation of default behavior may  still be something you or I don't like.

---

### Post by cariboo on 2013-12-27
The entire email conversation can be seen [here]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-December/014804.html").

---

### Post by Hungry Man on 2013-12-27
This is not even slightly a big deal. Of course it does this, otherwise you would have to enter your password before you could connect to wifi.

---

### Post by deadflowr on 2013-12-28
If someone can read that file, then you have bigger(much bigger) problems, as it is only readable/accessible/movable/copyable by root.

---

### Post by Linuxisfast on 2013-12-30
Encrypt your hdd and password protect it via BIOS and in no way they are getting to any of your passwords.

---

### Post by miguelpires on 2013-12-30
Hi,
For me is a little bit strange this situation. The average user don't need/have knowlege to encript the disk and set a Bios pass, and don't know that the pass of the wifi are in plain text. 
regards
Miguel

---

### Post by MG&amp;TL on 2013-12-30
> **miguelpires said:**
> Hi,
For me is a little bit strange this situation. The average user don't need/have knowlege to encript the disk and set a Bios pass, and don't know that the pass of the wifi are in plain text. 
regards
Miguel

The *average user* doesn't have access to the root account:

```
$ ls -l /etc/NetworkManager/system-connections/
total 4
-rw------- 1 root root 333 Dec 23 14:42 ####
```

```
$ cat /etc/NetworkManager/system-connections/####
cat: /etc/NetworkManager/system-connections/####: Permission denied 
```

In summary, unless the user is root (in which case they can read your passwords anyway), you can't read the file, so it doesn't matter.

---

### Post by buzzingrobot on 2013-12-30
All distros do this.

---

### Post by sffvba[e0rt on 2013-12-30
> **buzzingrobot said:**
> All distros do this.

I see you beat me to it :p

[http://news.softpedia.com/news/All-Linux-Distributions-Store-Wi-Fi-Passwords-in-Plain-Text-If-You-Don-t-Use-Encryption-412387.shtml]("http://news.softpedia.com/news/All-Linux-Distributions-Store-Wi-Fi-Passwords-in-Plain-Text-If-You-Don-t-Use-Encryption-412387.shtml")

---

### Post by miguelpires on 2013-12-30
Hi,
Thanks for the info!! I'm going to learn how to secure my kids PC!
Best regards
Miguel

---

### Post by Linuxisfast on 2013-12-30
> **miguelpires said:**
> Hi,
For me is a little bit strange this situation. The average user don't need/have knowlege to encript the disk and set a Bios pass, and don't know that the pass of the wifi are in plain text. 
regards
Miguel


The Ubuntu installer is the best in its class when it comes to partitioning and encrypting drive during install so I suggest you give it a try next time.

---

### Post by Habitual on 2014-01-02
Wireless Fidelity IS NOT SECURE to begin with.
The password being "clear" to "someone" is trivial.

---

### Post by r3dd on 2014-01-03
Just a thought, if you are not comfortable with plain text passwords you can uninstall Network Manager and use Wicd. Wicd encrypts the passwords for you. Once again, just a thought. It is LINUX, you can do whatever you want with it.

---

