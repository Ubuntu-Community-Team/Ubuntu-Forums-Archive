---
title: "Why doesn't debconf-set-selections work for the tripwire installation"
date: 2013-01-08
forum: Server Platforms
---

### Post by kevpatts on 2013-01-08
I'm trying to automate tripwire installation but I keep getting prompted for Site Keys no matter what I do.

On a fresh server install of 12.04.1 I should be able to do:
```
export TripWireLocalPassword=twlocalpw
export TripWireSitePassword=twsitepw

echo "postfix postfix/main_mailer_type select Internet Site" | sudo debconf-set-selections
echo "postfix postfix/mailname string `hostname`" | sudo debconf-set-selections
echo "tripwire tripwire/local-passphrase select $TripWireLocalPassword" | sudo debconf-set-selections
echo "tripwire tripwire/local-passphrase-again select $TripWireLocalPassword" | sudo debconf-set-selections
echo "tripwire tripwire/site-passphrase select $TripWireSitePassword" | sudo debconf-set-selections
echo "tripwire tripwire/site-passphrase-again select $TripWireSitePassword" | sudo debconf-set-selections
echo "tripwire tripwire/use-localkey boolean true" | sudo debconf-set-selections
echo "tripwire tripwire/use-sitekey boolean true" | sudo debconf-set-selections
echo "tripwire tripwire/rebuild-config boolean true" | sudo debconf-set-selections
echo "tripwire tripwire/rebuild-policy boolean true" | sudo debconf-set-selections
echo "tripwire tripwire/installed note" | sudo debconf-set-selections

sudo apt-get update
sudo apt-get install -y tripwire
```
and not be prompted for anything, but I still get prompted for the site and local keys. Is this a bug?

Kevpatts

---

