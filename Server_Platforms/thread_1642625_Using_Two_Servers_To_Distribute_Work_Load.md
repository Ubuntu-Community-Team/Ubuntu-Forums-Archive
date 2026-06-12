---
title: "Using Two Servers To Distribute Work Load"
date: 2010-12-10
forum: Server Platforms
---

### Post by garryconn on 2010-12-10
Ideally, I would like to set up a reverse proxy server so that my two computers can host websites. But I haven't had much luck setting that up. Instead, as an alternative, I had the idea of having my two servers work together and I wanted to get some opinions about that.

Does it make sense to have one server handle all the http port 80 requests and then designate the other server to handle all the mysql requests? Reason I am asking is I am wanting to host quite a few of my own websites from my home office. I'm already doing this now with one server and things are working great. 

Originally, in this post ([http://ubuntuforums.org/showthread.php?t=1642265](http://ubuntuforums.org/showthread.php?t=1642265)) I wanted to set up a second server and do reverse proxy, but I don't think I can figure out how to set that up and the more I think about it, maybe this new idea is better. Does anyone have any thoughts on this?

---

### Post by SeijiSensei on 2010-12-10
> **garryconn said:**
> Does it make sense to have one server handle all the http port 80 requests and then designate the other server to handle all the mysql requests?

One way to split the load is to put MySQL on one machine and have the HTTP server connect to it over the network.  I don't think that's proportionate to the loads involved, though.  My guess is the database transactions are more costly than parsing the page and sending out the resulting HTML by Apache. 

There are other load-averaging techniques that rely on nearly real-time updating of replicated databases.  I've never tried that myself.

Notice that you're creating a new potential point of failure for your services.  You'll now need to have both the web server and the DB server available 24/7.

Personally, I've never run websites that generate sufficient traffic to worry about problems like this.  Most servers I've run with Apache, PHP, and PostgreSQL on the same machine have load averages near zero.  And these aren't hefty machines, either.

---

### Post by elico on 2010-12-10
what are you trying to achieve by spread the load? like if you must have specific problem that you want to solve..
and most of the standard load problems can be solved by other means as load balancing..
you dont have a site like Wikipedia that reverse proxy will make a lot of different, am i right?

---

### Post by garryconn on 2010-12-10
Hi SeijiSensei and Elico. Thanks so much for your responses. I agree with you 100% It's nothing to parse a webpage compared to processing mysql queries. And totally, you're right about the dependancy of two machines. Setting up one server to handle all the http requests and one server to handle all the mysql wouldn't exactly be balanced. The mysql server would be working much much harder than the http server. 

Honestly, what I really WANT to do is build a small scale server farm. I just threw this idea out because I'm having so much trouble with creating a reverse proxy server. 

Here's what I really would like to do:

I have a very good Internet connection, and my ISP allows for customers to run servers. So I would totally like to take advantage of that. I know that I can continue to use HostGator and other web hosting companies for my websites. I'm not trying to avoid doing that. The purpose behind wanting to setup and maintain my own server farm here in my office isn't to try to save money, or things like that. The purpose is for the enjoyment, challenge, and education. I love computers and have great interest with Linux and web servers. It's something I want to learn more and more about. In return, this gives me more experience with maintaining live production servers. Who knows, I could even eventually land a neat job working for a web hosting company.

I want to build my own grid of servers. Right now I have two computers ready to go. The problem I am facing at the moment is that I only have ONE external IP address and can't figure out how to configure thins so that the second server can be accessed without having to add the port into the URL. I know that this all could be FIXED instantly by giving my ISP a phone call and ordering an additional IP address each time I add a new server. But, that negates the purpose of learning how to overcome this challenge. Another aspect of thinking on this situation is that IPV4 addresses are running short. So, why should I pay extra money and why should I use extra IPV4 addresses if I can build my server farm with one IP? I really don't NEED multiple IP addresses to do what I want to do. And I would much rather learn from this situation instead. 

That being said, I have two web servers setup and ready to go, but I only have one static IP address to use. 

I need one web server to handle all the traffic request and forward traffic to the correct server based on the domain name. For the time being until I add a third server to my grid, the first server will also hosts some sites as well. Once I add a third server, the main server will STOP hosting sites and act only as a reverse proxy server. 

The first server can remain port 80... that's fine. The second server can be configured for port 8080... that part is fine as well. But, I don't want people have to add the port number (i.e. :8080)  into the url of the domains hosted on the second server... or eventually third server, forth, etc..

Once again, after a lot of research, I have determined that the solution is to setup a reverse proxy server using Apache. But, I just can't quite piece all the various documentation together to successfully do this. I'm hoping that someone can offer me some guidance on that? Any help would be very appreciated. Thank you so much for taking time to read what I have posted so far. Anything I can do to help in return, by all means let me know.

---

### Post by ingeva on 2010-12-11
> **garryconn said:**
> 
Once again, after a lot of research, I have determined that the solution is to setup a reverse proxy server using Apache. But, I just can't quite piece all the various documentation together to successfully do this. I'm hoping that someone can offer me some guidance on that? Any help would be very appreciated. Thank you so much for taking time to read what I have posted so far. Anything I can do to help in return, by all means let me know.

Have you considered cloud computing? I think that's all the big ones are using, but there shouldn't be anything wrong with setting up a cluster of anything from 2 computers and up.

I know very little about cloud computing and have never tried it, but you can set it up from the Ubuntu 10.10 server CD. Then I believe you'd get load balancing and all will use the same IP address.

---

### Post by SeijiSensei on 2010-12-11
> **garryconn said:**
> Once again, after a lot of research, I have determined that the solution is to setup a reverse proxy server using Apache. But, I just can't quite piece all the various documentation together to successfully do this. I'm hoping that someone can offer me some guidance on that? Any help would be very appreciated. Thank you so much for taking time to read what I have posted so far. Anything I can do to help in return, by all means let me know.

I'd send all the requests to one of the machines. Then in the <VirtualHost> containers for some of the sites, set up a reverse proxy to send those requests to the other machine.  On that machine the <VirtualHost> containers would include the actual site definitions.

---

### Post by garryconn on 2010-12-13
Hi SeijiSensei

That's exactly what I want to do. I want to have a dedicatd computer for routing and forwarding traffic to different web servers in my grid. I'm having a lot of trouble figuring out how to setup a reverse proxy. 

In part of researching, I ran across a thread here where you were helping someone else with the same requests. Unfortunately, he wasn't as eager to learn and you grew frustrated with him, which is understandable. 

Could you point me in the right direction to some pages that do a great job explaining setting up proxy servers. The official documentation on the Apache page is hard to understand. The examples provided for each section tend to be too focused. It's hard to grasp the big picture on the configurations.

---

