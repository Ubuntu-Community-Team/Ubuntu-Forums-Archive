---
title: "How To: webserver with livebox"
date: 2009-03-03
forum: Server Platforms
---

### Post by SpikeyMike on 2009-03-03
I had another thread asking if anyone knew how to configure the orange livebox for use with a webserver, in my case apache2. I have since figured out how to do it and so have written this how-to. This worked for me so I hope it works for others.

First of all go to the livebox configuration page, usually 192.168.1.1

select the firewall tab and click on add

enter the following settings:

server name: apache
access activated: yes
protocol: TCP
port from 80
port to 80 
local ip address: (ip address of the computer running the server)


click on apply and save the settings

click on the advanced tab

move the mouse over the firewall tab and select NAT from the drop-down menu

click on the policy based NAT tab

there you should see the rule you just added but the status should be disabled

select it on the left hand side and click enable

save the settings


the web server should now be accessible from the internet as well as your home network.

regards

Spikey

---

