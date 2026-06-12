---
title: "PXE boot server"
date: 2012-08-04
forum: Server Platforms
---

### Post by Loki57701 on 2012-08-04
Hello everyone, 

Following this guide: [http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/](http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/)

I've tried to setup a PXE boot server for one of my older laptops. 

When I try to network boot the laptop I get a bunch of text flash on the screen for a split second, and the it takes me to 'boot:'. 

When I type in the name of the kernel to boot 'pxelinux.0' I get another quick flash of text that goes by to fast to make out, and then I'm brought back to the 'boot:' prompt. 

When I check my logs I see:

```

in.tftpd[2062]: tftp: client does not accept options
tftp/udp: bind: Address already in use

```


I've googled these errors, but I still wasn't able to fix this. 

I would appreciate any suggestions.

Thanks.

---

### Post by lykwydchykyn on 2012-08-04
Usually at the boot: prompt you'll be typing in the name of one of your configured boot options.  What is in your boot config file?

---

### Post by Loki57701 on 2012-08-04
That's a good question.

I don't remember seeing that in the guide I followed.

Can you elaborate more?

---

### Post by lykwydchykyn on 2012-08-05
In the tutorial, it's the file you create in steps 15-17.  The tutorial doesn't describe in in specific terms, though; what are you trying to pxe-boot?

---

