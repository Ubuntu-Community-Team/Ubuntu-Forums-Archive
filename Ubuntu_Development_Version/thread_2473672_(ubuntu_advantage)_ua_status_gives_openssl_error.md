---
title: "(ubuntu advantage) ua status gives openssl error"
date: 2022-04-10
forum: Ubuntu Development Version
---

### Post by ilgaz on 2022-04-10
Hello.

I remember having to remove many GUI update tools to get rid of blocking prompts on our company laptop which confuses workers/locks down the entire work.

I will be offline (health issues) for a month so I thought it would be a nice idea to enable livepatching/ unattended updates.

Here is what happens:
[FONT=monospace][COLOR=#000000]ua status [/COLOR]
Failed to access URL: [https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=5.15.0-25-generic&series](https://contracts.canonical.com/v1/resources?architecture=amd64&kernel=5.15.0-25-generic&series)
=jammy 
Cannot verify certificate of server 
Please check your openssl configuration. 

I did everything including importing the certificate of that host to the machine. Nothing changes. Is there a list somewhere that I can install or am I facing a beta bug here?
[/FONT]

---

### Post by jbicha on 2022-04-10
Ubuntu Advantage is only available for supported LTS releases. Ubuntu 22.04 is not a supported LTS yet (because it hasn't been released!)

---

### Post by ilgaz on 2022-04-14
Thanks for reply. I believe it is connected to a very major bug regarding Turkish UTF8 locale/openssl . Bug is so bad that even wget/curl doesn't work right with https. See what happens:
[FONT=monospace][COLOR=#000000]
locale [/COLOR]
LANG=tr_TR.UTF-8 
LANGUAGE= 
LC_CTYPE="tr_TR.UTF-8" 
LC_NUMERIC=tr_TR.UTF-8 
LC_TIME=tr_TR.UTF-8 
LC_COLLATE="tr_TR.UTF-8" 
LC_MONETARY=tr_TR.UTF-8 
LC_MESSAGES="tr_TR.UTF-8" 
LC_PAPER=tr_TR.UTF-8 
LC_NAME=tr_TR.UTF-8 
LC_ADDRESS=tr_TR.UTF-8 
LC_TELEPHONE=tr_TR.UTF-8 
LC_MEASUREMENT=tr_TR.UTF-8 
LC_IDENTIFICATION=tr_TR.UTF-8 
LC_ALL= 
[COLOR=#54ff54]**casaba@ship-macbook**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/backups**[/COLOR][COLOR=#000000]$ sudo locale-gen c [/COLOR]
ca_AD           ca_ES.UTF-8     ca_IT           ckb_IQ          cs_CZ           cy_GB.UTF-8 
ca_AD.UTF-8     ca_ES@valencia  ca_IT.UTF-8     cmn_TW          cs_CZ.UTF-8      
ca_ES           ca_FR           ce_RU           crh_UA          cv_RU            
ca_ES@euro      ca_FR.UTF-8     chr_US          csb_PL          cy_GB            
[COLOR=#54ff54]**casaba@ship-macbook**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/backups**[/COLOR][COLOR=#000000]$ sudo locale-gen C.UTF-8  [/COLOR]
Generating locales (this might take a while)... 
  C.UTF-8... done 
Generation complete. 
[COLOR=#54ff54]**casaba@ship-macbook**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/backups**[/COLOR][COLOR=#000000]$ sudo update-locale LANG=C.UTF8[/COLOR]

(logout/login)
[FONT=monospace][COLOR=#000000] ua status [/COLOR]
SERVICE       AVAILABLE  DESCRIPTION 
cc-eal        no         Common Criteria EAL2 Provisioning Packages 
cis           no         Security compliance and audit tools 
esm-infra     no         UA Infra: Extended Security Maintenance (ESM) 
fips          no         NIST-certified core packages 
fips-updates  no         NIST-certified core packages with priority security updates 
livepatch     no         Canonical Livepatch service 

This machine is not attached to a UA subscription. 
See [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


The exact issue causing this is there:
[https://github.com/openssl/openssl/issues/18039](https://github.com/openssl/openssl/issues/18039)[/FONT]

[/FONT]

---

