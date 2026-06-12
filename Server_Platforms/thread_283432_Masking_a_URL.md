---
title: "Masking a URL"
date: 2006-10-24
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-24
Hi all,

I am not really sure if / how i would go about this. or even what it would be called (i tried some googling but didnt get anywhere).  i have set up some virtual hosts on my server which all work grand. (my domain name is done though easydns as i have a dynamic ip).  My partner has a domain name that she pays to be forwarded only.  so at the mo its forwarded to a subdomain

partner.example.com

what i would like to know is, is it possible to mask My domain so it looks like they are still on hers.  her provider does two options. frame or http redirection.  with frame it does show as her url but what ever page your own it still only says partner.com rather than partner.com/cat/index.htm etc.  and the http it changes the url to partner.example.com

what i would like if poss is to have it look like she has full hosting somewhere but its being forwarded to my server.

i hope that made sense, as i said i dont even know if masking is the right turn or how to start to think to go about it.

any thoughts idea would be great..

thx all

Twiggy

---

### Post by twistedtwig on 2006-10-24
I was thinking about this at lunch.... as i said in my last post i dont know much about this area so could be wrong but i would guess to do that you would need to BE a FULL real world DNS server.

any thoughts?

---

### Post by MJN on 2006-10-24
I'm not sure I follow exactly what you want to do, and why..
 
Am I right in thinking that your want to host your partners website, using her domain name? If so, do it 'the right way' by configuring the DNS of your partners domain (via her current host/registrar) to resolve to your IP - either directly (which may require delegating the domain to a dynamic-ip-friendly DNS provider such as yours) or indirectly by configuring her domain as an alias for one of yours.
 
You really do not want to go down the route of framed forwarding (they are a pig for search engines, old browsers, text browsers, small-platform (e.g. mobile/cell phones) browsers) or http forwarding (URL changes as you say, unnecessary browser redirection, unnecessary points of failure in the chain) so aim for the ideal.
 
Unless there's a particular reason why you don't want your domains known it would be beneficial to say what they are then we can see who the current provider is and discover what options are available with regards to DNS (re)configuration at her end. If you just don't want all-and-sundry knowing the domain (if this is the case it probably shouldn't be on the Internet) then feel free to PM it to me and I'll have a look.
 
Mathew

---

### Post by twistedtwig on 2006-10-24
thx for the advice.

my partners site is footfaerie.me.uk

my site is ponywars.com  her subdomain is footfaerie.ponywars.com

so what i would like to do is have someone enter footfaerie.me.uk then it be redirected / forwarded (not sure of the correct word) to the subdomain on my server but still have the url of footfaerie.me.uk.

say someone clicked on links and it took you to footfaerie.me.uk/links/index.htm the url would say that rather than the subdomain of ponywars.com.

she uses 1and1.co.uk and as i say i use easydns.com

this is all rather new to me so bit confused (if you couldnt tell  by the way i am posting).. i hope this makes a bit more sense

thx

Twiggy

EDIT: had a look i can edit name servers if that is what you mean

---

### Post by MJN on 2006-10-24
Okay - that's a lot clearer now.
 
One thing I didn't ask - does your partner currently use e-mail under the footfairie.me.uk domain? (the DNS says there is, and it's 1and1 that handle it - but they could be forwarding the mail elsewhere). Given you didn't mention it I'm assuming you're not wanting to provide e-mail for her (i.e. just the web hosting) - this is important as it effects how the DNS to be configured.
 
First off, a little testing is probably in order just so you can prove the concept without screwing up her current web presence. I suggest setting up a sub-domain of footfairie.me.uk (actually just a test host record) and we can play with that before going the whole hog by doing the following (there are many ways to skin this cat but we'll start with the most straightforward):
 
1) Login to your partners 1and1 account and create test.footfairie.me.uk using their control panel and then configure test.footfairie.me.uk as an A record to your current IP. This is detailed at [http://faq.oneandone.co.uk/domains/dns_settings/11.html](http://faq.oneandone.co.uk/domains/dns_settings/11.html)
 
2) Now reconfigure the virtualhost settings for your footfairie.ponywars.com such that it also responds to requests for test.footfairie.me.uk (using the **Serveralias test.footfairie.me.uk** directive).
 
Hopefully the DNS propogation will be instantaneous (as its a new record the 1and1 servers should be queried directly for new lookups) and hence if you stick test.footfairie.me.uk into your browser you will hopefully get your partners website!
 
Note the smattering of *hopefully*'s there - before progressing let's make sure we get this far - report back when you're done and even if it's not working we'll be in a position to debug from there (by querying the DNS from this end, and connecting to your webserver also).
 
It may sound painful but it'll be worth sticking to this process to get what you want - when all is done we can go back to discuss exactly what has happened and why... but one step at a time!
 
Mathew

---

### Post by twistedtwig on 2006-10-24
woohh! /head blow up a little there :P will have to have a look at that when i get home from work. need to pay attention to that and not break something by mistake.

thx for the help.. will be back in touch soon :D

p.s.. nope email isnt a worry she uses hotmail for it all

---

### Post by twistedtwig on 2006-10-24
okie dokie,

so i couldnt figure out how to create a subdomain on 1and1.co.uk so i just forwarded footfaerie.me.uk directly to my IP.  i seem to be having issues with the virtual host i think

<VirtualHost *>
ServerName footfairie.me.uk
ServerAdmin [email]admin@ponywars.com[/email]
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


i can not get it to go to the footfaerie part it always goes to the root (ponywars.com)  i tried with and without the serveralias.

---

### Post by MJN on 2006-10-24
> **twistedtwig said:**
> 
<VirtualHost *>
ServerName footfa**i**rie.me.uk


Typo? ;) I can be forgiven for using an 'i' instead of 'e' throughout my post but you've got no excuses!

Incidentally, also add **Serveralias *.footfaerie.me.uk** in as presumably you want people to reach it on [www.footfaerie.me.uk](www.footfaerie.me.uk) (and whatever else they may happen to want to type before .footfaeries.me.uk!)

Working now?

Mathew

---

### Post by twistedtwig on 2006-10-24
i never did that.. honest... it must have been copy paste that did it ;)

well... OMG how cool is that.. it worked.

now just the minor detial of a dynamic ip :p

---

### Post by MJN on 2006-10-24
Well you're almost there so don't give up just yet!

You've got two options:

1) Transfer footfaerie.me.uk to easydns and update it in the same way as your ponywars.com domain (presumably you're using some client-side software?). I'm not familiar with easydns so don't know if this costs (if it does, consider using zoneedit.com - upto five domains for nowt)

or, 2) Configure the footfaerie.me.uk DNS at 1and1 such that it has a CNAME (alias) of ponywars.com. Hence, whenever your IP changes and your ponywars.com DNS changes lookups for footfaerie.me.uk follow suit!

I'd go with option 1 if possible - always good to have all your domains in the one place (and it'll let you play around with them at the same time if circumstances change in the future).

Mathew

---

### Post by twistedtwig on 2006-10-24
yep easydns.com is err £35 a year i think.. always like the service.  will have a look at zoneedit.com now and contact their support to see if the cname option is do able.

1and1.co.uk is err £4 ish a year so really cheap (my the misses likes it :p) but not sure they do that.. at least not on this package.

thx dude.

will post back when i find stuff out

Twiggy

OH and yep there is a script that gets run automatically on my comp that updates easydns.com each time my ip changes.

---

### Post by MJN on 2006-10-24
CNAMEs are part of the DNS standard (they're just a type of record, just as A and MX are) so anyone that offers DNS offers CNAMEs. Heck, even 1and1! [http://faq.oneandone.co.uk/domains/dns_settings/18.html](http://faq.oneandone.co.uk/domains/dns_settings/18.html)

£35/year sounds extortionate - I can highly recommended registering your domains via easy123 (like many, a few quid/year for a .co.uk) and delegating the domain to zoneedit.com - free unless you require the more 'fancy' services like backup mail servers etc (these require more than DNS config). For the dynamic IP update I use the zoneclient Python script running as a cron job.

Mathew

---

### Post by twistedtwig on 2006-10-24
cool,

cheers dude, you have been SOOO helpful its great.  I have registered with zoneedit.com.  but am having an ISSUE with 1and1.co.uk.  i can not change the name servers OR the CNAME i get a silly "this can not be done due to your status" message.  have gotten in touch with their help and fingers crossed will be solved soon enough.

can i just double check (making sure i understand, should do really)... CNAME would be footfaerie.ponywars.com as it is just a forwarding name / address?

thx again for the help :)

---

### Post by MJN on 2006-10-24
Assuming footfaeries.ponywars.com is an address that gets automatically updated when your dynamic IP changes then, yes, you would give both [www.footfaeries.me.uk](www.footfaeries.me.uk) and footfaeries.me.uk CNAMEs of footfaeries.ponywars.com.

One way of looking at CNAMEs is that if you've got **abc CNAME def** then when a client looks up abc they get told to instead lookup def to find the answer.

If you're going to be delegating both domains to zoneedit then I'd suggest leaving CNAMEs out of it (they can play havoc with mail, and can be a common cause of head-scratching debugging issues) and just manage the DNS for both your domains seperately. There's no reason your dynamic IP client cannot update both domains individually.

Mathew

P.S. If footfaeries.me.uk ends up at zonedit then you may as well at least set up mail forwarding such that ***@footfaeries.me.uk** gets redirected to her Hotmail account (this could be a chargeable service I'm not sure..)

---

### Post by twistedtwig on 2006-10-24
Hi Mathew,

well it turned out to be my lack of knowledge and understanding of the subject.  I had a thought jsut as i was about to go to bed.. now i had added the serveralias footfaerie.me.uk could i actually just do the http redirect and it show up correctly..

AND it did :) so just using their basic package seems to have worked with that extra line.  i do understand a lot more now.

although i am not 100% sure what that command means. will have to look it up tomorrow.  just tried writting some random address and it didnt work. (wanted to check that someone couldnt pretend to be someone there not that easily.  i am guessing there are ways but hell i dont know them ;) ).... 

thx so much for the help and advice its been really enlightening and productive.. always feels good to get a solution

Twiggy signing off for the night


EDIT: so i lied... i dont get it fully... just tried to do footfaerie.me.uk/footfaerie.html  and i get redirected back to the default virtual host becuase it doesnt match against the rest.  i presumed i would need to put a start after the name and alias to account for that but it didnt seem to work.. could be that i am rather tired and not thinking straight or something my brain hasnt cottoned onto yet.  

any thoughts ideas / slaps round head?

thx

Twiggy

example of star fingy ma bob
> <VirtualHost *>
ServerName footfaerie.me.uk*
Serveralias [www.footfaerie.me.uk*](www.footfaerie.me.uk*)
ServerAdmin [email]admin@ponywars.com[/email]
DocumentRoot /var/www/footfaerie


p.s... :p  dont know what i woudl do without putty

---

### Post by twistedtwig on 2006-10-24
i suppose i could set up multiple virtual hosts to redirect different options but that sounsd very messy.

right honestly gonna stop rabbiting to me self on here now

---

### Post by peanut butter on 2006-10-24
so ill sum up what you haveto do.
1. go to 1&1 and create cname from [www.footfarie.co.uk](www.footfarie.co.uk) to ponywars.com
2. redirect footfarie.co.uk to [www.foorfarie.co.uk](www.foorfarie.co.uk)
3. set up vhosts like you alredy probably have.
4. you should be ready to roll.
try taking out the * form the vhost lines containing the domains.
when using cnames it just uses the ip address of the target.
also with the ServerAlias derective you can put multiple aliases by separating them by a space " ".
hope this helps.

EDIt: also you cant CNAME the root of a domain name. and sorry for misspellings of domain names.

---

### Post by twistedtwig on 2006-10-25
i think i was being overly keen last night.  testing from local computer in network with webserver it seemed to work.  at work now and it doesnt :(

it is now redirecting back to footfaerie.ponywars.com

havent done the cname bit yet.  waiting for 1and1.co.uk to come back to me on the errors

---

### Post by MJN on 2006-10-25
It was all working last night (i.e. at message #13 - I confirmed this from this end)!! Why did you go and change things?!
 
The serveralias directive does not force any rewriting of the domain name and furthermore should not contain any *'s where you've put them!
 
The address rewriting in place at the time of writing is done by the client as a result of being served a redirect by the 1and1 web servers. DNS is not playing a role.
 
If you can afford the downtime setup a footfaerie.me.uk zone on ZoneEdit and, once supplied with the nameservers and set up some simple A records to your current IP address, delegate the zone from 1and1 to the zoneedit nameservers.
 
Then we can look at the automatic updating of the A records when your IP changes whether that by making the domain an alias of your ponywars one or configuring a dynamic client to do the job for you.
 
The bottom line is you do not want to be using http redirects (framed or otherwise) as they are a solution suitable only for when your hands are tied. Yours aren't - you have a reconfigurable web server, control of the domains, and a whole load of DNS providers able to host the DNS for you (for free) so do the job properly! ;) 
 
Mathew
 
**P.S. The reason you thought everything was working as desired last night even when you reverted back to http redirects was because your client/ISP still had the revised DNS records for footfaerie.me.uk in the cache and hence was completely oblivious to you changing things!**

---

### Post by twistedtwig on 2006-10-25
righttt.....

am still waiting for 1and1.co.uk to come back to me over C names or using my own name servers.  i kept getting an error last night

will have another go tonight and pay more attention ;)

i thought (obviously wrong) the only thing i changed was the way it gots its ip.  (where we had it pointing to my dynamic ip).

will keep you informed tonight.  and yep completely agree doing it proper is far better way.

Twiggy

---

### Post by twistedtwig on 2006-10-25
Hi guys,

ok so i think i am almost there. the cname bit seems to have worked today.  i redirected it to footfaerie.ponywars.com. peanut butter said i should redirect it directly to ponywars.com.  if i did that would it not think it was ponywars.com not the subdomain?

so if i use **www.**footfaerie.me.uk it works perfectly. but footfaerie.me.uk doesnt work it goes to the normal site.

> 
############### charlottes foot faerie home page #################

<VirtualHost *>
ServerName footfaerie.me.uk
Serveralias [www.footfaerie.me.uk](www.footfaerie.me.uk) footfaerie.me.uk
ServerAdmin [email]admin@ponywars.com[/email]
DocumentRoot /var/www/footfaerie
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On
</VirtualHost>


from what i understood i should be setting up two serveralias's for [www.ff](www.ff) and just ff as above but it didnt seem to work (or it was that i didnt allow dns to refresh.  but i didnt think this was a dns issue.  i thought the ip was resolved to ponywars.com and apache sorted out the redirections at that point.  (i did restart apache).

thx for all your help guys u all rock :D

---

### Post by MJN on 2006-10-25
It's working fine from here - both [www.footfaerie.me.uk]("http://www.footfaerie.me.uk") and footfaerie.me.uk resolve correctly and result in the correct site. (Incidentally, I'd suggest changing the font colour, or putting a suitable contrasting background on as it's quite hard to read! ;))

Given you mentioned about 'doing the job properly' you might want to change your CNAMEs slightly.. Currently you've got:

[B] footfaerie.me.uk.       IN      CNAME   footfaerie.ponywars.com.
footfaerie.ponywars.com. IN      CNAME   ponywars.com.
ponywars.com.           IN      A       86.139.24.124[/B]

The 'cascading' CNAME is unnecessary and results in an extra lookup - better to point the CNAME directly to ponywars.com.

Other than that, top job!

Mathew

---

### Post by twistedtwig on 2006-10-25
cool bananas... i was vpn'd into work to test from outside my network.  the dns server there can be funny at times.  tried to change the cname from footfaerie.ponywars.com to ponywars.com but got that poopy error again.  think they dont allow many changes or something.  anyway will hope its saved if not try it again soon and THANK YOU SO MUCH FOR YOUR HELP!!!

feel well happy really mad my day, and I imagine charlotte wont be too displeased when she finds out as well :)

Twiggy

OH p.s... the colour schema was NOT my choose.. i am just the monkey the organ grinder makes the calls ;)

---

### Post by twistedtwig on 2006-10-26
just wanted to say thank you again.. well pleased with it.

also how could i check the route info you gave.  ie did you just know from deduction that it was doing 3 steps or is there a command to check this sort of thing?

thx again.. /one very happy chappy

Twiggy

---

### Post by MJN on 2006-10-26
It's just a case of querying the DNS. There are various tools for doing it but one the de facto standard ways is using 'dig' e.g. **dig **[**www.footfaeri.me.uk**]("http://www.footfaeri.me.uk")** A **queries the DNS for the A record and you'll see the CNAMEs/aliases in the answer section.
 
You might prefer a higher level online tool such as [www.dnsstuff.com]("http://www.dnsstuff.com") - specifically the 'DNS Lookup' function. Also, [http://www.dnsstuff.com/tools/lookup.ch?name=footfaerie.me.uk&type=A](http://www.dnsstuff.com/tools/lookup.ch?name=footfaerie.me.uk&type=A) also details the lookups times for each step so you can see how long the additional lookups are taking... in this a good few 1/10ths of a second! ;) (even longer when ns33.1and1.co.uk is down - seems to be happening rather a lot at the time of writing!)
 
Mathew

---

### Post by twistedtwig on 2006-10-26
bargin :D

---

