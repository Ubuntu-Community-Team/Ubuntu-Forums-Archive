---
title: "Super noob here, need some guidance and answers"
date: 2009-04-23
forum: Server Platforms
---

### Post by Tron8 on 2009-04-23
Hello everyone, I live in a fraternity and we were thinking of setting up a server for our house.  I've asked around and everyone seems to agree that an Ubuntu server is one of the best options, so I have some questions.

1.  How easy is it to set up a file and print sharing server in a house that runs mostly Vista, with some XP and Mac users, especially for someone who has _never_ used Linux or Ubuntu before?
2.  Would it be possible for me to monitor and limit the bandwidth of users on our network as well?
3.  How hard will it be to secure this server against people outside the network?
4.  What kind of machine would I need to accomplish 1 and 2, right now we have a P4 1.8Ghz with 512mb of RAM not being used that we were thinking of converting, it has a lan card and built in ethernet on motherboard.
5.  How much work will this require to set up?

Any and all input is appreciated, preemptive apologies for my noobness.

---

### Post by jasonsjunk on 2009-04-23
Here is my two cents on this.  Yes Ubuntu wouold make an excellent choice for what you want to accomplish.  That old P4 should do the job just fine although I would probably bump the ram to 1 gig or more if possible.  

1) I would use the desktop version of Ubuntu it is much easier for new users to deal with.  
2) Download and install Webmin to help you admistrate many of the functions via a web browser, some of the configuration tools make things much easier than having to search for and manually edit the confiuration files for programs like Apache, Samba, etc.  
3) Samba will take care of your print and file sharing but you will have to do some reading on this one, there are a lot of resorces available and many people on this board have posted working configurations.  However for the print sharing I have found that a seperate print server plugged into your router is a much easier option and it doesn't require the printer to be near the server.  
4) When you say monitor and limit the bandwidth of the users on your network what are you trying to prevent?  In order to throughly control and monitor all network bandwidth you will have to set up a proxy server which is something that you shouldn't attempt till you are more proficient with Linux it is not an easy task.  If you are just trying to control access to your network most home routers can accomplish that on thier own.  If you want to attempt this I would check our eBox which is a router, firewall distribution based on Ubuntu.  Either way I would read up in the networking section of this forum for the best ways this can be accomplished.  
5) Remember to come up with a good backup policy and stick with it, you don't want all of the files on your file server to disappear due to a hard drive crash.

---

### Post by kamaji792 on 2009-04-23
Here is my 1 cent worth.

jasonsjunk seems to have covered most of it.

I think the ubuntu server setup is the best I have ever come across.  Not that I have used many distributions.  I just followed the ubuntu server instructions from the link below:

[url="https://help.ubuntu.com/8.04/serverguide/C/index.html"]
https://help.ubuntu.com/8.04/serverguide/C/index.html[/url]

I would say download the server iso and give it a go.

I opt to do a base install. i.e. I don't install any apps. Set the domain name to "localhost".

As it is a server set it to a static IP address.

Then when it re-boots I do an update:

```
sudo apt-get update
sudo apt-get upgrade
```

I like the command line so I install OpenSSH and use Putty to access it from Windows.

Install the bits you want and get them to work one at a time.

If you have any issues then I am sure you will get lots of help on the forums.

All the best.

---

