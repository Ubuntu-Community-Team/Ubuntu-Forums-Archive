---
title: "Squid - Denied File Type Downloads"
date: 2008-08-21
forum: Server Platforms
---

### Post by whitegourd on 2008-08-21
For a few days now, I though I may have had squid working the way I wanted it to, but just recently, a user brought to my attention that he wasn't able to access "gmail.com", due to an attempt to download a blocked file extension from the denied filetype download list (acl). He would get past the login screen, but quickly gets hit with the file blocked message.

Turns out that when logging in from FF3 or IE6, we could log in just fine, but IE7 won't allow it because in the long URL there is a ".com" at the end which is really referencing the log in account, not an actual executable file extension.  Why is it that FF3 and IE6 doesn't interpret the url as a file extension download ...? I don't know.  But IE7 is seeing it as such.

denied_filetypes.acl
```

\.(ade)$
\.(adp)$
\.(app)$
\.(bas)$
\.(bat)$
\.(chm)$
\.(class)$
\.(cmd)$
\.(com)$
\.(cpl)$
\.(crt)$
\.(exe)$
\.(fxp)$
\.(hlp)$
\.(hta)$
\.(ins)$
\.(isp)$
\.(jse)$
\.(lnk)$
\.(mda)$
\.(mdb)$
\.(mde)$
\.(mdt)$
\.(mdw)$
\.(mdz)$
\.(msc)$
\.(mp3)$
\.(msi)$
\.(msp)$
\.(mst)$
\.(ops)$
\.(pcd)$
\.(pif)$
\.(prf)$
\.(prg)$
\.(reg)$
\.(scf)$
\.(scr)$
\.(sct)$
\.(shb)$
\.(shs)$
\.(url)$
\.(vb)$
\.(vbe)$
\.(vbs)$
\.(wsc)$
\.(wsf)$
\.(wsh)$
\.(zip)$

```

I had to remove the "com" from the acl list for now until I can figure out how to actually block the ".com" executables from getting downloaded.

Is there another string I could use to allow the access of gmail and yet fend off users that attempt to download .com files at the same time?  I'm out of ideas at the moment.

---

### Post by whitegourd on 2008-10-01
Ok, I finally figured this thing out after some additional testing.  Since Squid utilizes these filters from top to bottom of the squid.conf file, I adjusted the squid.conf file so that the "whitelist" filter is above the "denied_filetypes" filter. (I had it reversed before).

My squid.conf was originally configured this way which blocked the .com domain extension when trying to log into gmail.com and not an actual executable .com file.
----
#Denied_Filetypes
#Whitelisted
#Blacklisted

Now it is configured this way so that I can still prevent users from downloading .com files from other sites with the exception of gmail.com
----
#Whitelisted
#Denied_Filetypes
#Blacklisted

After including "gmail.com" in the whitelist, I was able to place the \.(com)$ line back into "denied_filetypes.acl" list so that it can still block other users from downloading any .com files from other sites.

(side note) ... webchat in gmail.com can still be blocked even though gmail.com is in the whitelist.  This is because the webchat is trying to communicate with "http://chatenabled.mail.google.com" (google.com) domain.

---

### Post by Greettat on 2008-10-01
success grows out of struggles to overcome difficulties.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

