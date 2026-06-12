---
title: "Webmin package for dapper 6.06"
date: 2006-06-14
forum: Server Platforms
---

### Post by blkish on 2006-06-14
hi

i've just moved back to Ubuntu from CentOS as a desktop platform. I'd also like to use it as a server platform, but one key thing that's preventing me at the moment is the lack of a Webmin package from any repository i have found thus far.

i've installed the 'old fashioned' (manual) way for my desktop, but a crucial to my server deployments is the availability of all installed packages from distribution-specific repositories. and webmin is my admin tool of choice, kinda important..

does anyone know what the status/likelihood of a Webmin package for Ubuntu 6.06 or later is? i read rumours that the debian Webmin package maintainer was no longer maintaining the package, but no reference to a sucessor.

thanks

blkish

---

### Post by localzuk on 2006-06-14
I think you are going to be out of luck. A lot of people dislike webmin due to its apparant insecurity. Personally, I would advise that you spend a little time learning how to do things via the terminal and use ssh to connect instead.

What sort of tasks are you actually doing via webmin? As I could advise on a different approach?

---

### Post by blkish on 2006-06-14
[QUOTE=localzuk]I think you are going to be out of luck. A lot of people dislike webmin due to its apparant insecurity. Personally, I would advise that you spend a little time learning how to do things via the terminal and use ssh to connect instead.

What sort of tasks are you actually doing via webmin? As I could advise on a different approach?[/QUOTE]

thanks for the info, i thought that might be the case

i'm fully capable of doing everything on the console, but as i'm no longer an admin by trade, the time i have to spend on administrative tasks on the various servers i'm responsible for is limited.
therefore i find a GUI which cuts down the time required to perform mundane duties very useful indeed. also i may not touch a system for long periods, so having everything neatly, visually, laid out can be extreemely helpful.

there is an inherent security risk in running any application/service which runs with sufficient privilleges to alter system configuration/data, however in my case at least the benefits far outweigh this.

only allowing connections to eg webmin via VPN or tunneled ssh also manages the risk quite effectively.

it's a shame though that there's no likelihood of a package, as i'm not aware of another tool which comes close the the breadth of functionality within webmin.

again thanks for the response, have a good day!

blkish

---

### Post by Macchi on 2006-06-14
Can't we use Webmin restricted to a tunnel through SSH with long & safe keys and no passwords and even Denyhosts? That would probably solve part of the many security issues.




( Warning: A few more thoughts about manual server configuration:

I am interested on the practical applications of Webmin or other tools for GNU/Linux/BSD server installation, configuration, administration and maintenance (yes, the holy grail for a server) . It would mean a lot for increasing the number of installations and market share for small business servers.

As a professional I would like to be able to install and maintain easily say 20 Ubuntu servers for small offices. But presently I could barely make a living on such a business here in my home market. Therefore I look for repeatable and safe ways to scale up these tasks aroung server installation and maintenance. 
Just by using a suitable distros and making manual copies of configuration files I could partially achieve a goal of scalability, but manual methods would not work for say 200 small offices. Thus I am presently only an artisan, not an industrialist.

My point is that I appreciate the handicraft, beauty and elegance behind manual server configuration but if Linux and Ubuntu are going to take the world in a industrial scale it would be a priority to have high-level tools for server maintenance. I hope that I am not offending anyone other than strict proprietary interests on server software)

---

### Post by localzuk on 2006-06-15
I think you are way wrong there my friend. The one place where linux *is* popular is in the server market.

If you want to configure 20 servers by altering files, all you need do is do it on one and copy the files to each server. Whereas in something such as Windows Server you need to set each one up using slow graphical tools.

Maintenance can mostly be automated using cron jobs and emails to your mailbox to inform you of the status of such things.

An example of where linux is becoming more popular is the voluntary community in the UK. More and more organisations are switching their systems over to linux. These organisations are usually maintained by one person who does a whole load of them. The extra time that would be needed to look after windows machines would mean that the person would not be able to maintain as many systems.

Another place where linux is popular is Universities. For example, Lancaster University runs a huge number of linux servers for many different tasks. Most of the techies/systems teams prefer linux due to the speed at which things can be done via terminal commands rather than having to trawl through endless gui tools.

---

### Post by Macchi on 2006-06-15
Regarding Webmin and its benefits vs disadvantages:
Has anyone tried the Mepis SOHO server? I would love to see such a solution for Ubuntu! It is a live CD with a small office/home offfice server (almost) ready for use.  Among other things it can configured with Webmin. 









Regarding the philosophical component of this thread I should certaily move this discussion to the Ubuntu café. But before that let me just mention two things:

Firstly, my customers in small companies are asking for "out of the box" solutions for simple servers. The Ubuntu LAMP install is a good step in that direction but there is more to be done by simplificating the installation and configuration process. Remember that for one or two decades ago it was quite difficult for the average business user to get started with email and information services on the web. The trend is most probably to simplify the way users interact with IT-services and thereby the way they interact with servers.

Secondly, the world never stops and there is no rest in a dynamic market. Regarding webservers I just read that besides a clear dominance for Linux+Apache, the numbers have been turning downwards while the proprietary competition have been growing lately: 
> Microsoft continues to gain share in the web server market, chipping away at Apache's commanding lead. The number of hostnames on Windows servers grew by 4.5 million, giving Microsoft 29.7% market share, a gain of 4.25% for the month. Apache had a decline of 429K hostnames, and loses 3.5% to 61.25%.

Apache's lead over Microsoft, which stood at 48.2% in March, has been narrowed to 31.5%, a shift of 16.7% in just three months.
How and why can this happen? 
(it was just a rethorical question!)
Source: [http://news.netcraft.com/archives/2006/06/04/june_2006_web_server_survey.html](http://news.netcraft.com/archives/2006/06/04/june_2006_web_server_survey.html)

And by the way localzuk, we are both right! Command line interfaces and graphical interfaces are very cool indeed! :)

---

### Post by lutosdemayo on 2006-06-15
[QUOTE=Macchi]
Source: [http://news.netcraft.com/archives/2006/06/04/june_2006_web_server_survey.html](http://news.netcraft.com/archives/2006/06/04/june_2006_web_server_survey.html)

[/QUOTE]
I for one was really searching webmin to administer my system much like CPanel does. And i do agree that to move forward Linux needs these graphical tools. 

The netcraft survay may be true about the spike in the usage of Windows in the server space but we should remember that GoDaddy just transfered their parked domains to a Windows server with a little coaching from Microsoft. They said Microsoft made their $$$$ work.

---

### Post by localzuk on 2006-06-15
Cpanel and webmin do completely different things really. Cpanel is rather specialised to cover the needs of a webhosting server whereas webmin covers *everything*. If you want some sort of free hosting panel, try something like [http://web-cp.net/](http://web-cp.net/) [http://kandalaya.org/vishwakarma.shtml](http://kandalaya.org/vishwakarma.shtml) [http://www.xpanel.com/](http://www.xpanel.com/) or [http://www.alternc.org/](http://www.alternc.org/) which are more specialised.

Your comment regarding the change from linux to windows at godaddy is exactly right. Throughout the netcraft historical charts you will see sudden huge changes from one type of server to another. This is nearly always due to a large company changing their serverbase, it isn't actually a *real* change in popularity of a webserver IMO.

---

