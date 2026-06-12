---
title: "Nagios check_http will not work"
date: 2011-08-02
forum: Server Platforms
---

### Post by joker535 on 2011-08-02
I have a working nagios setup. It monitors all my Windows servers with no problem but it is a pretty basic setup. I want to add a function that will go out and look at text on a web page hosted on one of the servers. If the text is there then its OK and if it is not then it is failed. I have done some searching and found that check_http would be the command for that. I added the following to the cfg file for that server (urls and string content changed):
[I]
define service{
        use                     generic-service
        host_name               staticserver
        service_description     Railo Monitor
        check_command           check_http -w 10 -c 15 -H [http://test.test.com](http://test.test.com) -u [http://test.test.com/check.cfm](http://test.test.com/check.cfm) -s "egg salad"
        }[/I]

With this in the machines cfg file nagios fails the check upon restart. Commenting these lines out and it will pass so I know it is this service.

This service was intended to monitor Railo. If Railo is working properly then the cfm page called will display the text *egg salad*. If not then it will have something else. The cfm page works fine from both firefox on my workstation and lynx command line browser on the server. Then I try to use the check_http string from the command line and I get the following error:

[I]Name or service not known
HTTP CRITICAL - Unable to open TCP socket[/I]

It doesn't make sense that nagios can't see it but a web browser on the same server can see it fine. Apparently I am doing something wrong with both the cfg file and calling from the command line but I don't know what.

Any suggestions?

---

### Post by Habitual on 2011-08-02
what is your "define host" definition for staticserver?
does it include an 'address 123.456.789.012' entry?

does c```
check_http -w 10 -c 15 -H http://test.test.com -u http://test.test.com/check.cfm -s "egg salad"
``` work from c-li?
Try removing the 'use generic-service' call in your "define service", restart nagios and try the command manually from c-li.

---

