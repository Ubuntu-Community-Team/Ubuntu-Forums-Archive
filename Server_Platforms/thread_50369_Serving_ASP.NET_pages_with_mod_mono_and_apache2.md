---
title: "Serving ASP.NET pages with mod_mono and apache2"
date: 2005-07-20
forum: Server Platforms
---

### Post by ben ogle on 2005-07-20
Well, I *finally* got mod_mono working on my ubuntu box. I did quite a bit of searching so i thought I would post up and tell you folks some of the notable things I learned about it. 

First of all, dont use the deb/ubuntu package. It is mono v1.0.5 or something which doesnt come with windows forms and many other things as well. Compile it from source. Its really not all that difficult. I originally installed the apt-get package then tried to use the mod_mono package but nothing worked. I had also read that there were problems with the package on apache2, which I am using. So I found this guide and followed it pretty closely:

[http://www.codeproject.com/cpnet/introtomono2.asp](http://www.codeproject.com/cpnet/introtomono2.asp)

Essentially all you have to do is download and install mono, xsp, mod_mono, then add a few lines to some config files. So go to here:

[http://go-mono.com/sources/](http://go-mono.com/sources/)

And download mono, xsp, and mod_mono. Then you tar -xvzf whatever-package.gz and cd into the unzipped directory. At the command line run ./configure --prefix=/usr then make, then make install. 

To install mono I needed a crapload of utilities I did not have. Most, though, could be downloaded from the apt-get install goodness. 

I originally tried to install all the mono stuff with a prefix /etc because I thought apache was installed in /etc (I used the package), but it had a lot of problems installing xsp because it could not find any of the utilities it needed. So I ended up installing everything with --prefix=/usr. Also, I ran into an odd make error with mod_mono. When i tried to compile it I got this error:

apxs:Error: no config variable PREFIX

After searching I found the solution was to run this in the command line when in the mod_mono unzipped directory:

sed -i -e 's/ -S PREFIX="$(prefix)"//' src/Makefile.in

Once I got everything installed I, of course, had more problems. XSP was working fine. But when i added the module to apache and all the info I needed to the config files I was getting a "503: Service Temporarily Unavailable" error. This was a big problem because it seemed like no one was having the same issue. Well it turns out that this error occurs when there is no unix socket file created for mono. The mod-mono-server app is supposed to create this file but it was not. So I looked in the apache logs and there were errors concerning the version of corlib. It needed 37 and I had version 22. It was looking at the version of mono I had installed from the package. So I uninstalled all the packages and I reinstalled the 3 apps (it broke mono when i uninstalled the packages, then xsp was broken when I reinstalled mono). I restarted apache and it worked!

Then to allow other folks to see it I put this in the apache config file:

<Directory /the/dir/of/the/asp/pages>
  Order Allow,Deny
  Allow all
</Directory> 

and everything worked. 


More links:
[http://www.gotmono.net/documentation/mod-mono-howto.html](http://www.gotmono.net/documentation/mod-mono-howto.html)   
[http://www.mono-project.com/Mod_mono](http://www.mono-project.com/Mod_mono)
and there is an INSTALL file in the mod_mono source download.

I hope this helps someone out.

Ben

---

### Post by Hikaru79 on 2005-07-20
This DEFINETLY helps me out. You should mark it as a HOWTO and ask somemod to move it to the HOWTO forum. This is great!

---

### Post by Mr. Electric Wizard on 2005-08-12
I wonder when Mono will be taking on ASP.NET 2.0?
That is going to be the ULITMATE solution, I can't wait!

---

### Post by rush_ad on 2005-10-15
i think i need more help. how do i test the i have setup mono correctly?

---

### Post by hallikpapa on 2006-02-28
Anyone know what compilers I need to have installed to do this?

Also, anyone got ASP.NET 2.0 working?

I have some intranet pages from work built in Windows I want to see if they can be hosted on an ubuntu box.

---

### Post by ifeelcool.com on 2006-04-26
Hello after a few nights of programming i got it finally working..... Not really only a pre-compiled project worked..... :(
I have been trying to build my own simple hello world app, but it is not working.

What is the best way to create/compile/run an asp.net application?
I have tried the following for compiling:
-```
mcs /t:library /out:./bin/Program.dll Program.cs
```
Adding to config files:
-```
mod-server2-admin add --path=/var/www/program --app=program
```
-edit /etc/apache2/mods-enabled/mono.conf adding lines:
```

Alias /program "/var/www/program"
AddMonoApplications default "/program:/var/www/program"
<Location /program >
    SetHandler mono
</Location>

```
-finally i surf to [http://localhost/program/](http://localhost/program/) and then i am getting the error it **can't not find Program.dll**

And one other question, do i need to add the parameters -r:System.* to the mcs command?

Any help on building a ASP.Net application on ubuntu apache2 would be nice!

---

