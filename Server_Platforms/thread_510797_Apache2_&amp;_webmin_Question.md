---
title: "Apache2 &amp; webmin Question?"
date: 2007-07-27
forum: Server Platforms
---

### Post by Jolly-Swagman on 2007-07-27
After reading through the forum on Apache2 setups for my Ubuntu 7.04  web server I did eventually get it going, but also read about Webmin to administer it locally, so have installed Webmin and it seems to have undone all of the config files ie- http.conf. apache2.default, apache2.000 sites available and site enabled, also my sites avail and enabled now only have  this one line <NameVitualHost *80> in all the configs.
So after more reading about Webmin and this [http://www.webmin.com/apache.html]("http://www.webmin.com/apache.html")

My question is do I have to make the <VitualHost> for webmin as described in the link post or have I just done something wrong for webmin to delete and change all the files as described above.

I just spent hours and hours redoing all my sites avail and sites enabled files and the apache2 defaults from the bak files had saved restarted Apache2  and went into  webmin and all the <VirtualHosts> and files were really messed up so reinstalled webmin restated apache2 server and the same thing all the files have been undone to only this one line for each <NameVirtual*80> and of course you get the error that apache cannot file the files for the servers ie my site that were created and that there was a syntax  line error on line 22,, syntax error line 189, well there would be as the files the errors were for are not there anymore

So back to the question above to use webmin do I just only create <VirtualHost> for webmin and configure the rest from webmin interface, as I thought webmin implemented with apache not against it, or am I still missing something?
Still very new at these things but have learnt alot from the countless hours reading through tutorials and manuals but maybe I have just missed something simple I hope.

Any assistance most appreciated with thanks, as I thought I had all the hard work done, only to be undone.


Jolly Swagman

---

### Post by Jolly-Swagman on 2007-07-29
Well I,m still having problems with webmin it seems to be fighting with apache2 lol, so maybe i,ll just get rid of it and go back into the server room and just totally reconfigure apahe2 web file from there, as know one has any solutions as yet, and I have read almost every thing I can find on the subject, or as stated I just maybe missing something simple

Jolly Swagman

---

### Post by rfs1970 on 2007-08-02
Hi Jolly...

I am having a  hard time trying to set my ubuntu server and webmin as well...
I found [this book]("http://books.google.com.br/books?id=FyU8EjG-tf0C&dq=Managing+Linux+Systems+with+Webmin&pg=PP1&ots=fpkgHNcubF&sig=Z4iOpdnmd02j-1kVCH-3HdVKLR8&prev=http://www.google.com.br/search%3Fhl%3Dpt-BR%26client%3Dfirefox-a%26rls%3Dcom.ubuntu%253Aen-US%253Aofficial%26hs%3Djnm%26q%3DManaging%2BLinux%2BSystems%2Bwith%2BWebmin%26btnG%3DPesquisar%26meta%3D&sa=X&oi=print&ct=title") that maybe could help you to find some answers.

r.

---

### Post by Viruk on 2007-08-03
Did you install webmin from a package? or do it manually?

I have done all my installations of webmin manually with the newest release and not had any trouble. I have done this a couple of times with version 1.320 and last week with 1.350 and not had any trouble.

Do you really need to mess about with a virtual host? Even though the apache webserver is better, will you really notice a difference? Maybe someone could chip in here and give some reasons why it would be worth it...

My notes on how I set up webmin:

Download the latest version (1.360 released yesterday) of webmin and copy the tarball to the /usr dicectory on the desired Ubuntu machine (you can use WinSCP to do this easily if you are a windows user). 

Log on to the Ubuntu machine (or use PuTTY to connect to it) and type: 

cd /usr 
sudo tar xzvf webmin-1.360.tar.gz 
sudo apt-get install libnet-ssleay-perl
cd webmin-1.360
./setup.sh /usr/local/webmin
Leave config file directory as default (hit enter) 
Leave Log File directory as default (hit enter) 
Leave Full path to perl as default (hit enter) 

Set web server port to any port you like (default is 10000) 
set Login name to admin 
Set a Password 

Select Y for use ssl 
Select Y for webmin at boot time 

Log in to Webmin by typing the following in to a browser: 
[http://[ip-of-server]:10000](http://[ip-of-server]:10000) (assuming you used the default port - substitute the 10000 for the port you specified if you used a different port to the default)
Where XX is the ip address of your Ubuntu Server. 

These notes were for my new technician at work so they are pretty step by step - hth

---

### Post by Viruk on 2007-08-03
btw - you may need to use https instead of http when accessing webmin if you choose secure access

---

### Post by Jolly-Swagman on 2007-08-11
Thanks for the info I think Webmin is  not where it should be we reinstall and thanks for the book link will have a good look at that too.

Sorry for not getting back sooner havent been well recently both the wife and myself have been ill so have not even been in the server room.

Again many thanks will get back to you all with results and hopefully all will be up and running.

Jolly Swagman    :guitar:

---

