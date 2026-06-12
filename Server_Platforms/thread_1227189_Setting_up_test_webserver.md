---
title: "Setting up test webserver"
date: 2009-07-30
forum: Server Platforms
---

### Post by TUOggy on 2009-07-30
I am trying to teach myself php and sql so that I can work more with web apps.  I have never set up a webserver so I decided to do a nice little google search for some quick and dirty tutorials.

I followed the instructions word for work (except for the static IP, because of some weird networking issues) from this page discussing how to set up a web server for development...

[http://www.maverickconceptions.com/2009/04/26/a-designersdevelopment-environment/](http://www.maverickconceptions.com/2009/04/26/a-designersdevelopment-environment/)

Here's the problem.  Now every time I try to restart Apache I get the following error:

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/passenger.load: Cannot load /usr/lib/ruby/gems/1.8/gems/passenger-2.2.1/ext/apache2/mod_passenger.so into server: /usr/lib/ruby/gems/1.8/gems/passenger-2.2.1/ext/apache2/mod_passenger.so: cannot open shared object file: No such file or directory
                                                                         [fail]

Line 185 of /etc/apache2/apache2.conf is:

Include /etc/apache2/mods-enabled/*.load

I'm stuck and I can't even get Apache to load on a restart now...

Please help me...

PS - I'm sure there are better ways to set up a webserver.  I really don't want to scrap this setup is at all possible.  I already have everything setup, and if this error is fairly easy to fix then I would prefer to just use this setup...

---

### Post by wojox on 2009-07-30
What you need to do is go here:

```
/usr/lib/ruby/gems/1.8/gems/passenger-2.2.1/ext/apache2/
```

and look for mod_passenger.so

See if it's there and check the file permissions.

---

### Post by TUOggy on 2009-07-30
okay so there isn't a passenger-2.2.1, it's version number 2.2.4 so the folder name is passenger-2.2.4.

Where do I need to change that so that it is looking in the right folder?

---

### Post by TUOggy on 2009-07-30
As a temporary fix I just copied the passenger folder and renamed the copy to passenger-2.2.1

This has allowed me to boot up apache again...

so here's the problem now...

Now that everything is supposedly running properly, I can access "domain.com" but can't access "bob.domain.com"

I don't know if there are other settings i need to change in apache or passenger, but it still isn't working the way the tutorial said it would (although it is working well enough to work)

Thanks for the help.

---

### Post by TUOggy on 2009-07-30
Wow... okay I feel dumb now.

In /etc/apache2/mods-enabled/passenger.load I just changed the folder names from passenger-2.2.1 to passenger-2.2.4

```

LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.2.4/ext/apache2/mod_passenger.so
PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.2.4
PassengerRuby /usr/bin/ruby1.8
RailsEnv development

```

although I am still unable to access "bob.domain.com"

---

### Post by hessiess on 2009-07-30
> although I am still unable to access "bob.domain.com"

You need to set up a virtual host for the dommain "bob.domain.com".

---

### Post by Kolipoki on 2009-07-30
> although I am still unable to access "bob.domain.com"Remember that most changes to the Apache files will need to restart or reload the Apache server. Ex:

```
sudo /etc/init.d/apache2 restart
```Cheers, good luck!

---

### Post by TUOggy on 2009-07-30
> **Kolipoki said:**
> Remember that most changes to the Apache files will need to restart or reload the Apache server. Ex:

```
sudo /etc/init.d/apache2 restart
```Cheers, good luck!

Yeah, I tried that.  I'm not able to get it to work like the tutorial said...

Instead I have just decided to do it the old fashioned way and stick with domain.com/bob.

No reason to waste more time on something that is easily enough fixed this way.

---

### Post by TUOggy on 2009-07-30
> **hessiess said:**
> You need to set up a virtual host for the dommain "bob.domain.com".

Is that not what was explained in the tutorial?

/etc/apache2/sites-enabled

create bob

```

sudo gedit bob

```

Then tell it where to listen:

```

<VirtualHost *:80>
ServerName bob.domain.com
DocumentRoot /home/username/workspace/clients/bob/www/
</VirtualHost>

```

I have done all this, and I still can't access the page with this setup.

It is easy enough to just use "domain.com/bob" so that will fix it, but it would be interesting to figure out what I did wrong...

---

### Post by R.Bucky on 2009-07-30
did you enable the sub-domain with sudo a2ensite? Also, did you add the sub-domain with your registrar?

---

### Post by TUOggy on 2009-07-31
> **R.Bucky said:**
> did you enable the sub-domain with sudo a2ensite? Also, did you add the sub-domain with your registrar?

I didn't think you had to use the a2ensite/a2dissite commands the way this was set up.  Isn't that taken care of when I add the virtual hosts file to "/etc/apache2/sites-enabled"???

So do you have to register the sub-domain with the registrar when you are staying within your local network?  I thought that was something that Apache/Passenger took care of.

---

### Post by bolerodan on 2009-07-31
If this is your local network, how are you accessing said "domain.com" Did you modify your /etc/hosts file? A personal DNS server?

If its a presonal DNS server, you will have to add an entry for bob.domain.com. Apache does not just create subdomains out of virtual hosts. Subdomains are DNS controlled and not apache controlled. Apache just listens for those domains/subdomains and serves it.

If you did it the /etc/hosts way, add in an entry bob.domain.com and have the IP point to your webserver.

Otherwise Im not sure how you are controlling your domain access.

---

### Post by TUOggy on 2009-07-31
> **bolerodan said:**
> If this is your local network, how are you accessing said "domain.com" Did you modify your /etc/hosts file? A personal DNS server?

If its a presonal DNS server, you will have to add an entry for bob.domain.com. Apache does not just create subdomains out of virtual hosts. Subdomains are DNS controlled and not apache controlled. Apache just listens for those domains/subdomains and serves it.

If you did it the /etc/hosts way, add in an entry bob.domain.com and have the IP point to your webserver.

Otherwise Im not sure how you are controlling your domain access.

I followed the directions here:
[http://www.maverickconceptions.com/2009/04/26/a-designersdevelopment-environment/](http://www.maverickconceptions.com/2009/04/26/a-designersdevelopment-environment/)
word for word.

I was trying to achieve the exact same results.  I have not changed the /etc/hosts file in any way.  I am using an extra domain that I had registered for use earlier this year that I am no longer using.  I have it redirecting to 192.168.1.* (my local server address).  From the author's descriptions, there is no need to edit the hosts file or to add subdomains with my registrar.

Now, for practical use, I have abandoned this way of doing it, and when my domain name expires, I will abandon this tutorial altogether.  I was just curious if I am correct in interpreting the tutorial as complete and I am making a mistake on my server, or if there are additional steps that need to be taken that are missing from the tutorial, and thus my server.

I am currently accessing my test server using domain.com/site.  When my domain name expires with my registrar, I will go with ip.com/site or I will change my hosts file (but probably just go with the ip address since I don't want to change my hosts file on all 6 or so of my network computers).

But like I said before, this is a big learning experience for me, so I am just trying to appease my curiosity.

---

### Post by bolerodan on 2009-07-31
okay, thats what I needed to know. (i only brought up the hosts file because I had no idea of your domain/DNS situation). You have a real registered domain name pointing to your network. Good.

The tutorial did not essentially talk about subdomains.

I'm assuming you properly set up a wild card resource entry into your Registrar account?

You need to realize that Subdomains are all DNS controlled. Essentially what he did was put a wildcard so that any subdomain or any amount of characters would resolve to your IP address rather than manually entering all subdomains. (since you have 1 address, Subdomains could essentially point to another webserver, so you would not use the wildcard entry in your DNS)

so blahblah.yourdomain.com, yourdomain.com or even bob.yourdomain.com would all resolve to your IP because of the wildcard resource entry.

if that doesnt work for some reason, manually put in an A record or CNAME and create the subdomain at your registrars name server.

you can also use the dig command on linux to see what resources are reutnred from a DNS query. Also, pinging your subdomain can also tell you if its working.

If you are interested it, take some time in to see how DNS,subdomains and how virtual hosts in apache really work. Subdomains are not Specific to apache or webservers, therefore not Apache controlled. You cannot have a domain say "bolerodan.com" and set up apache to look for "dev.bolerodan.com or linux.bolerodan.com" because there are no zone resource records for those.

Good luck and hope you experiment to figure out whats going on.

---

### Post by TUOggy on 2009-08-03
> **bolerodan said:**
>  Subdomains are not Specific to apache or webservers, therefore not Apache controlled. You cannot have a domain say "bolerodan.com" and set up apache to look for "dev.bolerodan.com or linux.bolerodan.com" because there are no zone resource records for those.

Good luck and hope you experiment to figure out whats going on.

Okay, so I understand that I need to set up a wildcard subdomain, but how will simply setting that up with the registrar direct that to the subdomain on my network?

ie.  I set up *.domain.com.  I set up a bob folder in my web directory in apache  (/home/name/websites/bob).  I want bob.domain.com to point to that directory, so I set up the virtualhost file per the instructions in the link provided.  What other steps need to be taken?

---

### Post by TUOggy on 2009-08-03
I figured it out.  Apparently GoDaddy isn't the most wildcard subdomain friendly registrar out there, but after much looking I found that I just need to put an entry in the A(Host) entry with * as the host and my IP in the points to field.  Every other place told me to use CNames...

Thanks everyone for all the help.  Couldn't have done it without you.

---

