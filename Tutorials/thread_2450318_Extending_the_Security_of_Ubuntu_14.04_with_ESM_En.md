---
title: "Extending the Security of Ubuntu 14.04 with ESM Enabled"
date: 2020-09-11
forum: Tutorials
---

### Post by EuclideanCoffee on 2020-09-11
Extended  Security Maintenance is a Canonical service for the Ubuntu desktop and  server. Its ethos follows the model of Debian&#8217;s Extended Long Term  Support, where older repositories of Debian software called packages are  maintained by a small pool of professional developers to extend the  lifetime of Debian&#8217;s release.

Though ESM is an option, it is not a  permanent solution, and it should be used to factor in new projects.  All new projects should use the latest LTS on the start of development.  For example, you wouldn&#8217;t want to build an application exclusive to  Windows 7 in 2020. ESM provides projects 2 additional years  whereas the support window would&#8217;ve closed much earlier. This allows  projects with long development like various engineering projects.

You will need to enable ESM support for your operating system. This is done through the Ubuntu Advantage service.

If you do not have an account, [create one here.]("https://ubuntu.com/advantage")

Then install the UA client on your desktop/server.

$ sudo apt update
$ sudo apt install ubuntu-advantage-tools

You can check your account status on Ubuntu 14.04 ESM in the following manner.

$ sudo ua status

Your output would read something like this.

```

$ ua status

SERVICE       AVAILABLE  DESCRIPTION
cc-eal        no         Common Criteria EAL2 Provisioning Packages
esm-infra     yes        UA Infra: Extended Security Maintenance
fips          no         NIST-certified FIPS modules
fips-updates  no         Uncertified security updates to FIPS modules
livepatch     yes        Canonical Livepatch service


This machine is not attached to a UA subscription.
See https://ubuntu.com/advantage
```

This machine is not attached to a UA subscription.
See [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

Now  that you see this, you should have to sign into your ua account. Run  the following command to attach your account&#8217;s token to this computer.

$ sudo ua attach YOUR_TOKEN

Once your machine has been attached to your account, you can enable esm with the following.

$ sudo ua enable esm-infra

You should now see this whenever prompting for status.

```

$ sudo ua status

SERVICE       ENTITLED  STATUS    DESCRIPTION
cc-eal        yes       n/a       Common Criteria EAL2 Provisioning Packages
cis-audit     no        &#8212;         Center for Internet Security Audit Tools
esm-infra     yes       enabled   UA Infra: Extended Security Maintenance
fips          yes       n/a       NIST-certified FIPS modules
fips-updates  yes       n/a       Uncertified security updates to FIPS modules
livepatch     yes       disabled  Canonical Livepatch service

Enable services with: ua enable <service>

     Account: user@domain.tld
Subscription: user@domain.tld

```


Congratulations.  You now have ESM enabled for your 14.04 ESM device. Learn more about  ESM here. Follow me for more articles on Linux security and Ubuntu  development topics.

---

### Post by hess88 on 2020-09-11
Thanks. 

When I install I see 
```
ubuntu-advantage-tools is already the newest version.
```

But when I try ```
ua status
```, I get ```
ua: command not found
```.  Is there a path problem I need to fix on ua?

---

### Post by EuclideanCoffee on 2020-09-14
What happens when you place a sudo at the beginning?

sudo ua status

---

### Post by Saptarshi_Roy on 2020-09-20
> **EuclideanCoffee said:**
> What happens when you place a sudo at the beginning?




It is still the same - > sudo: ua: command not found

---

### Post by EuclideanCoffee on 2020-11-24
Oh, you likely did not install the tool. I thought I forgot to include it, but I did not.

Here is how you install it.

```

$ sudo apt update
$ sudo apt install ubuntu-advantage-tools


```

If this is not working, try re-installing by removing the package and installing it.

```

$ sudo apt install ubuntu-advantage-tools

```

---

