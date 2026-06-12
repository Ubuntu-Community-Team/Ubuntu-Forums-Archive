---
title: "GNS3 with Guake terminal HOW TO"
date: 2012-01-08
forum: Virtualisation
---

### Post by majster on 2012-01-08
Hi!

Recently I installed guake terminal on my pc and I need to say its awesome [http://guake.org]("http://guake.org/") ;) 

I found it very nice and easy to use Guake as terminal for GNS3. Here is what you will need to changed in your GNS3 configuration after installing guake ( [apt://guake](apt://guake) )

Go to:  Edit / Preferences
then navigate to: General / Terminal Settings
And "terminal command" bar replace with: ```
guake -t -n %d -r %d -e 'telnet %h %p' >/dev/null 2>&1 &
```Now when you click twice on router in gns3 guake will toggle down and activate new tab named the same as device you connecting to.

Enjoy :popcorn:

---

