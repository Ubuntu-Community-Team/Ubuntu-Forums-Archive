---
title: "Ubuntu Advantage is really free for personal use?"
date: 2020-04-30
forum: Security
---

### Post by Portaro on 2020-04-30
I'm on Ubuntu 14 and read that ubuntu advantage is free for personal use so I use my ubuntu one to log and register and this give me a command to terminal but I dnt receive any e-mail on the ubuntu one account connected.

The service is free for users of 14.04?

---

### Post by deadflowr on 2020-04-30
I don't think I have ever gotten a confirmation email for anything Ubuntu SSO outside of registering.
You got a token right?
Did you add it and check ua status
```
ua status
```


I think there is a caveat as covered in this:
[https://ubuntu.com/blog/ua-services-deployed-from-the-command-line-with-ua-client]("https://ubuntu.com/blog/ua-services-deployed-from-the-command-line-with-ua-client")
Which requires the hwe kernel which I think was the 4.4 kernel.

---

### Post by Portaro on 2020-04-30
Thanks blog link I dont find anything writed about this.

The command line return &#8594;
```

ua status
SERVICE       AVAILABLE  DESCRIPTION
cc-eal        no         Common Criteria EAL2 Provisioning Packages
esm-infra     yes        UA Infra: Extended Security Maintenance
fips          no         NIST-certified FIPS modules
fips-updates  no         Uncertified security updates to FIPS modules
livepatch     yes        Canonical Livepatch service


This machine is not attached to a UA subscription.
See https://ubuntu.com/advantage

```

---

### Post by EuclideanCoffee on 2020-04-30
If you check the wiki, it's quite clear what you should do to enable the service.

ua enable <service>

Have you done this? More info. [https://wiki.ubuntu.com/UAclient](https://wiki.ubuntu.com/UAclient)

To enable ESM.

ua enable esm-infra

---

### Post by Portaro on 2020-05-01
Only I wnat know is if the service is free because I dont receive any mail confirmation.

I apply the wiki method commands and now the service appear like this :

```

sudo ua status
SERVICE       ENTITLED  STATUS    DESCRIPTION
cc-eal        yes       n/a       Common Criteria EAL2 Provisioning Packages
cis-audit     no        &#8212;         Center for Internet Security Audit Tools
esm-infra     yes       disabled  UA Infra: Extended Security Maintenance
fips          yes       n/a       NIST-certified FIPS modules
fips-updates  yes       n/a       Uncertified security updates to FIPS modules
livepatch     yes       n/a       Canonical Livepatch service



```

Thanks.

---

### Post by EuclideanCoffee on 2020-05-01
The output shows that you are entitled esm-infra now that an account has been added.

[https://ubuntu.com/esm](https://ubuntu.com/esm)

> 
[COLOR=#111111][FONT=Ubuntu]Ubuntu Advantage for Infrastructure is available for physical servers, virtual machines, containers, and desktops. Free for personal use.
[/FONT][/COLOR]

I do not think you need an email then to prove that it is free to you, as your account level has given you access.

> 
[COLOR=#333333][FONT=&amp]For Ubuntu 14.04 LTS as shown above, ESM will be automatically enabled after attaching the UA client to your account. After ubuntu-advantage-tools is installed and your machine is attached, ESM should be enabled. If ESM is not enabled, you can enable it with the following command:
[/FONT][/COLOR]
$ sudo ua enable esm-infra

[COLOR=#333333][FONT=&amp]With the ESM repository enabled, you may see a number of additional package updates available that were not available previously. Your system may have indicated that it was up to date before installing the ubuntu-advantage-tools, but make sure to check for new updates with **apt update**. If you have cron jobs set to install updates, or other unattended upgrades configured, be aware that this will likely result in a number of package updates after ESM is enabled.
[/FONT][/COLOR]

---

### Post by Portaro on 2020-05-01
Thanks for the help.

---

