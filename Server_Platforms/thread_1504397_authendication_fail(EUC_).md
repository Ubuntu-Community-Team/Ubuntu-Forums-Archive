---
title: "authendication fail(EUC )"
date: 2010-06-07
forum: Server Platforms
---

### Post by ypwu1 on 2010-06-07
Recently I am setting up Ubuntu private cloud platform, I followed installation instruction but on the setting, When the step:
"sudo -u eucalyptus ssh-copy-id -i ~eucalyptus/.ssh/id_rsa.pub eucalyptus@<IP_OF_NODE>" processed, authentication fail happened. so what the solution and how could I solve it.

Anyway, is there any professional discuss group of EUC?

---

### Post by suseendran.rengabashyam on 2010-06-08
Hi,

Try the following steps

1) In the target controller i.e the node controller(NC), temporarily set a password for the eucalyptus user:
> sudo passwd eucalyptus

2) On the Cloud Controller(CC) run:
> sudo -u eucalyptus ssh-copy-id -i ~eucalyptus/.ssh/id_rsa.pub eucalyptus@<IP_OF_NC>

once it prompts for a password, enter the password of the user 'eucalyptus' which you had created in Step 1.

3) Remove the password of the eucalyptus account on the node controller(NC):
> sudo passwd -d eucalyptus

For a comprehensive UEC guide try

[http://cssoss.wordpress.com/](http://cssoss.wordpress.com/)

Hope this helps.

---

### Post by ypwu1 on 2010-06-08
I have reinstall and follow the same instructions but still get "Authentication can't be host' and
Now try logging into the machine, with "ssh 'eucalyptus@192.168.206.11'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting."

Is that means ssh login with certification was failed. how to solve it?

---

### Post by suseendran.rengabashyam on 2010-06-09
Hi,

I assume 192.168.206.11 is the IP Address of the NC.

If the execution of

> sudo -u eucalyptus ssh-copy-id -i ~eucalyptus/.ssh/id_rsa.pub eucalyptus@192.168.206.11

was successful

then when you execute

> ssh eucalyptus@192.168.206.11

you will not be prompted for the password of the user 'eucalyptus'.

Hope this helps.

---

