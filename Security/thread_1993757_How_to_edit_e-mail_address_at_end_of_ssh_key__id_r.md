---
title: "How to edit e-mail address at end of ssh key  id_rsa.ub"
date: 2012-06-02
forum: Security
---

### Post by yeehi on 2012-06-02
I generated a ssh key using a virtual box installation of ubuntu.
I looked at the text inside the id_rsa.pub file and at the end there was an email address listed to [email]yeehi@virtualBox.ubuntu[/email].

I don't want that e-mail in my key. I want to use a different e-mail.

I tried editing the exported .pub file with my new e-mail address and then saved the file. I exported the .pub file to a different directory and checked the e-mail address. It wasn't at the end, though the old one had disappeared. 

I can generate a new key from scratch, if necessary. I don't need to use the one I have.

I don't know how to do it. Please help.

---

### Post by josephmills on 2012-06-02
That is not your email that is 
<username>@<Computer name>

there are some tutorials located here 
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

and also a good one 
[https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair](https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair)

---

### Post by yeehi on 2012-06-02
Thanks for the useful links and the help, josephmills.

I changed the ubuntu username, so that is good. I don't know how to change the host name. I had a look but couldn't see anything.

How do I change the hostname?

When I have done that, I will create a new key and I should be happy with that.

---

### Post by yeehi on 2012-06-02
Thanks for the useful links and the help, josephmills.

I changed the ubuntu username, so that is good. I don't know how to change the host name. I had a look but couldn't see anything.

How do I change the hostname?

When I have done that, I will create a new key and I should be happy with that.

---

### Post by Lars Noodén on 2012-06-02
The text at the end of the public key is not a mail address per se, it is officially a comment and it is optional.  So it is OK to leave it blank, but you could put in whatever text you want.  The other [fields](https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.7E.2F.ssh.2Fauthorized_keys) which precede the optional comment are an optional list of login options, the key type (ssh-dss or ssh-rsa) and the key itself encoded as base64.

You can go in with a text editor (vi or nano) and change the comment to whatever you want.

---

### Post by CharlesA on 2012-06-03
> **Lars Noodén said:**
> The text at the end of the public key is not a mail address per se, it is officially a comment and it is optional.  So it is OK to leave it blank, but you could put in whatever text you want.  The other [fields](https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.7E.2F.ssh.2Fauthorized_keys) which precede the optional comment are an optional list of login options, the key type (ssh-dss or ssh-rsa) and the key itself encoded as base64.

You can go in with a text editor (vi or nano) and change the comment to whatever you want.
Yep.

You can also generate a key with a different comment by using:

```
ssh-keygen -b 4096 -C "Some comment"
```

---

### Post by yeehi on 2012-06-03
Oh, that is very handy to know, CharlesA.

Do I wrap my comment inside quotation marks:

```
ssh-keygen -b 4096 -C "This is my comment"
```

or do I leave the quotation marks out?

```
ssh-keygen -b 4096 -C This is my comment
```

---

### Post by CharlesA on 2012-06-03
I think you need quotes. I always quote things with spaces as a general rule.

---

### Post by kevdog on 2012-06-03
Not to point out the obvious, but you do know you can edit the key in something like vi or gedit and just change the comment at the end.

---

