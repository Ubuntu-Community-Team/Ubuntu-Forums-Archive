---
title: "EXIM4 config - fgdn error"
date: 2011-04-15
forum: Server Platforms
---

### Post by spindler on 2011-04-15
I have recently installed EXIM4 mail server on my Ubuntu 10.10 server. 

I am using the following document to run the configuration.     [https://help.ubuntu.com/10.10/serverguide/C/exim4.html](https://help.ubuntu.com/10.10/serverguide/C/exim4.html)

I received the following error after running   **[FONT=monospace][/FONT]sudo dpkg-reconfigure exim4-config**
[COLOR=DarkSlateBlue]hostname --fqdn did not return a fully qualified name, dc_minimaldns will not 
work. Please fix your /etc/hosts setup.
 * Stopping MTA for restart                                                    
hostname --fqdn did not return a fully qualified name, dc_minimaldns will not 
work. Please fix your /etc/hosts setup.
                                                                         [ OK ]
 * Restarting MTA                                                        [ OK ][/COLOR]

[FONT=Verdana]I am not sure what this error is referring to.[/FONT]   My "hosts" file looks like this.

[COLOR=Blue]191.108.1.190	PowerEdge-200	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	PowerEdge-830	localhost6.localdomain6	localhost6
127.0.1.1	PowerEdge-200

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/COLOR]

I have not finished the configuration as described by the EXIM4 server document. I still need to run 
**sudo update-exim4.conf**.  However I did test the server to see if it send email and I was able to get an email sent to an external address.

Any idea why this error means?  How do I fix it?

---

