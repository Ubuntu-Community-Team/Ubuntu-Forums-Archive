---
title: "UEC - cant ssh into image - public key denied"
date: 2010-04-07
forum: Server Platforms
---

### Post by UltraDangerLord on 2010-04-07
Hello All,

I have recently set up a Ubuntu Enterprise Cloud system, I installed the cluster controller and 4 separate node machines.

I followed this guide in particular:

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

I'm at the very last step, the image is up and running but I'm having issues connecting to it. The command seems fine, it asks me to accept the rsa - for known hosts, I accept and then it responds with (public key denied)

Any idea what to do ? :confused:

-Thanks in advance

---

### Post by stlsaint on 2010-04-07
have you put the public key of your key pair into the authorized_keys file on the server?

---

### Post by UltraDangerLord on 2010-04-07
I'm not exactly sure what you mean,So I'm pretty sure I haven't done that. But I'm a bit confused. I created the mykey.priv, but I'm not aware about a public and private one ?

could you please describe this process in more detail for me please ?


This is the command to connect and the error
```

lepotar@cluster-controller:~/.euca$ IPADDR=$(euca-describe-instances | grep emi-DFC81082 | grep running | tail -n1 | awk '{print $4}') ssh -i ~/.euca/mykey.priv ubuntu@192.168.211.1
The authenticity of host '192.168.211.1 (192.168.211.1)' can't be established.
RSA key fingerprint is 76:a1:44:71:cf:40:57:60:70:ea:17:51:cb:6e:1d:14.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.211.1' (RSA) to the list of known hosts.
Permission denied (publickey).

```

I also did a search for authorized_key and displayed the results here

```

lepotar@cluster-controller:/var/lib/eucalyptus/.ssh$ locate authorized_keys
/usr/share/man/man5/authorized_keys.5.gz
/var/lib/eucalyptus/.ssh/authorized_keys
lepotar@cluster-controller:/var/lib/eucalyptus/.ssh$ cat /var/lib/eucalyptus/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA7vCMB+ddvUsheW0rQ2peBYbCCI98ScG9xxW20XxUTt1+LeGpLDc3ukciB0JlgnDtc1FZfi95BnQQO4mAFP/8tJ9oRrpetI7DV8Vtx0vcZq2N5pemPLKK1npkQQ/Gb8abBwaPV5fXczutZK9FXkJC1lfa+WxulljhbZRyW8KTnTTvgHiOd0SfIJ8rrJ3MYWaVMdqb/t3OVRwSTBgEc6+wIrYGL9Z64GXhDo+63tGdhe8WKUtvfe3R8bsY/rdi2v9pLkaxKtT8/MieGQJ+pFoT0cRWdmqnrzLdxxm5zl40iFrd2AzxxO5x07dPWThtQ/1xjsXB/fC1DkEa+TMSDSIILw== eucalyptus@cluster-controller
lepotar@cluster-controller:/var/lib/eucalyptus/.ssh$

```

do I have to put this file on the nodes ? the install guide didn't describe this step, what to do next ? :confused:

---

### Post by UltraDangerLord on 2010-04-08
Bump - Thinking of redoing the whole thing.... before I do, any suggestions ?

---

### Post by kiranmurari on 2010-04-09
Hi,

If you are using the store images, the ssh key injection takes place automatically.
If you are bundling and using custom images, you need to take care about the key injection during bundling process.
I have got UEC working with a 2 machine setup, able to sue store images and bundling Linux and Windows custom images.

The following links might be helpful:
[http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec](http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec)
[http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/](http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/)

---

