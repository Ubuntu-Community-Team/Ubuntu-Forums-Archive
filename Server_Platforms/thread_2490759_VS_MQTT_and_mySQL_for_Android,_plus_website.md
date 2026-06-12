---
title: "VS MQTT and mySQL for Android, plus website"
date: 2023-09-14
forum: Server Platforms
---

### Post by robuntu66 on 2023-09-14
Hi, 

I had a server at university last year with one dedicated IP address that I set up an MQTT Ultrawideband project.
It went well but I need to do it now I have come back to the UK and also want to run some other projects at the same time simultaneously. 

1. Run the MQTT Broker again and store in a MongoDB.
2. Host a mySQL database that android app can access for an experiment. 
3. Host a website, just a few pages that gather ethics checkbox information and stores responses in another mySQL database that is completed before the people run the app.

I have seen Fasthosts offer a service that I could use virtually with Ubuntu 22, they offer full root access, but is there anything I should consider you might know about them and any alternatives? Features I should consider, or advice that might be useful?

Thanks R

---

### Post by TheFu on 2023-09-15
Which programming language do you know?  That will massively change what is easy.

---

### Post by robuntu66 on 2023-09-16
Hi @thefu

Thanks for coming back to me.

[COLOR=#000000]1. Run the MQTT Broker again and store in a MongoDB - **The broker is in Python I set it up myself on Ubuntu before. I also need it to use that DB as later will use AWS IoT when scaling up potentially.**[/COLOR]
[COLOR=#000000]2. Host a mySQL database that android app can access for an experiment **- The android app is in Java Ive not had any problems using the QiSDK which is a Softbank Robotics project**[/COLOR]
[COLOR=#000000]3. Host a website, just a few pages that gather ethics checkbox information and stores responses in another mySQL database that is completed before the people run the app -[/COLOR][B][COLOR=#000000] I can write HTML, CSS, and implement this easily BUT note below will probably just copy a Wordpress template I have.[/COLOR]

[/B][COLOR=#000000]To add to that I can write C++ to a fair level, hardware prototyping etc, and use Linux shell easily.[/COLOR][B][COLOR=#000000]
[/COLOR]
[/B]The question is about the online server with SSH I could probably manage to configure everything but if there was a panel or I could install a panel to use that would be a bonus. Fasthosts offer their Virtual Private Server with 1x IP address for £5 a month and Plesk for £9.99 a month (too expensive). I was thinking that I could install a panel myself if they offer full root access.

I'm guessing I can just go for one IP address and still run MQTT on port 8883, and then set up 3306 and I could use a Wordpress easily I already have the files for a template I own I can FTP straight in onto port 8080. I can use my CloudFlare account to protect the system DNS Proxy and make it HTTPs without having to worry about setting up certificates. It isn't important to have it bulletproof because it is only for the student projects. I will back it all up a lot in case.

The key thing is to keep the cost down. £5 is cheap from their service... Well it seems cheap but that is why I am asking because I don't want to commit to £60 contractually and have overlooked something. I don't think I can find cheaper than that but I might be overlooking something and lose my money. 

Depending upon what you or people here say of course I will ask them about the port handling. I guess they might have a problem with people using another control panel for the server because it disrupts their business model, they might blacklist adding Plesk, maybe others but would that be possible anyway if you have full root access? Not sure. I guess if it is in some kind of Kubernetes / KubeVirt system 'virtually' then they might be able to I don't know enough about how that might be set up.

Best wishes,
R

---

### Post by robuntu66 on 2023-09-17
Hi @thefu
and anyone else based on what I said please let me know what you think. I've provided as much info as I can.
I want to get on with a purchase.

---

### Post by TheFu on 2023-09-17
You are doing things in a way that I'm not qualified to comment about.

---

### Post by robuntu66 on 2023-09-18
Hi
OK, thank you. I went with IONOS and took the £1 a month plus VAT and will split them out into two servers. 
One can be just for MQTT and MongoDB and the other can be for the mySQL databases and Wordpress.
I went with them because they are cheaper, and thy offer Plesk for free rather than any high charge rate, plus I can confirm the compatibility of MQTT here:
[https://www.support.aceautomation.eu/knowledge-base/how-to-install-a-cloud-mqtt-broker-on-a-vps-virtual-private-server/](https://www.support.aceautomation.eu/knowledge-base/how-to-install-a-cloud-mqtt-broker-on-a-vps-virtual-private-server/)
Have a nice day :_)

---

