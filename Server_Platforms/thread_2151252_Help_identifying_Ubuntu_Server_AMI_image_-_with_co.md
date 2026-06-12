---
title: "Help identifying Ubuntu Server AMI image - with control panel"
date: 2013-06-03
forum: Server Platforms
---

### Post by trivenisarees on 2013-06-03
[COLOR=#000000][FONT=verdana]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I'm looking for the right configuration & AMI for an EC2 medium server hosting, subject to the following constraints:[/FONT][/COLOR]
[LIST=1]
[*][COLOR=#000000][FONT=verdana]We've a lot of experience with Ubuntu & its command line tools - so my personal preference is to go with Ubuntu. What is the different between Ubuntu & Ubuntu Server? I guess I can go with Ubuntu server. Or is it better to look at another Linux variant?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=verdana]We'll be hosting 2 domains - the 2nd domain hosting may later merge with the first (in 3-4 months). The guys who manage the servieces have a preference for a Control panel (as opposed to simple ssh that I do) - so we want to run a control panel, with clear resource partitioning / virtualization between the domains - so that they don't interfere. We're neutral about the control panels - CPanel & Plesk are something we've used, so we have a preference for this. However, we did not find an AMI Ubuntu Server image with either. Is another control panel suggested for Ubuntu? Are they are installation issues?[/FONT][/COLOR]
[*][COLOR=#000000][FONT=verdana]&#8203;[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Both domains will be running LAMP - one also hosting Magento. So, an AMI image with Ubuntu Server 13.04, one of the control panels, and LAMP stack will be ideal. Any suggestions?[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=verdana]Thanks,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Arvind[/FONT][/COLOR]

---

### Post by Habitual on 2013-06-04
[http://cloud-images.ubuntu.com/locator/ec2/](http://cloud-images.ubuntu.com/locator/ec2/)
[http://alestic.com/](http://alestic.com/)

bookmark them.

[COLOR=#000000][FONT=verdana]The guys who manage the services with a preference for a Control panel is scary![/FONT][/COLOR]
Screams inexperience. IMO

but I have 20 years in IT and I still need a cp now and then. How about Webmin?

cPanel and Plesk cost big bucks.

---

