---
title: "Can't transfer .ogg files over http"
date: 2008-06-03
forum: Server Platforms
---

### Post by pytheas22 on 2008-06-03
This question isn't exactly specific to Ubuntu, but I'm hoping someone here might have some suggestions for me.

I have some web space from godaddy.com.  I know, their hosting is terrible--really slow server, their convoluted site looks like garbage and they do sketchy things to try to trick me into buying stuff I don't need--but the hosting is free right now and I'm using it until I can set up my own server.

I uploaded a .ogg file to the site, and when I try access it by opening [http://mysite.com/myoggfile.ogg](http://mysite.com/myoggfile.ogg) in a web browser, the file doesn't download.  Instead, I just get a blank page that says "OggS" at the top.  The permissions on the file should be alright, and I can download it over ftp without a problem.  I can also download other media files from the site, like .mp3s, without any issues.  It's just when trying to access .ogg files via http that it doesn't work.

I'm tempted to just blame the problem on something stupid that godaddy does with its hosting, but before trying to deal with their customer service, I wanted to check to see if anyone here might know of any reason that this would occur.  Is there some kind of glitch that I need to work around to share .ogg files over http, or any other reason other than godaddy's incompetence that this would occur?  I don't have too much experience with servers and http so maybe I'm just missing something...

---

### Post by windependence on 2008-06-04
You're blaming a lot on GoDaddy that is probably your won fault. First off, your hosting is FREE, what do you expect? That means they are supporting your hosting by using ads and selling you services and products. If you read carefully instead of just checking yes every time, you won't get sucked into buying all that crap. Their support is good, but they are a business and as such they have to make money like everyone else. If you are so disatisfied, why don't you get paid hosting?

I suspect that the reason you can't d/l these files is actually a security feature on thier server so people can't just download your entire site and steal it, ever thought of that? There are settings in Apache that can be changed to permit d/l certain file types. You really need to get on the phone with them and have them set you up.

-Tim

---

### Post by MJN on 2008-06-04
What's the URL? (PM me if you'd prefer)
 
It sounds like an issue with how GoDaddy deals with .ogg files (or files whose MIME-type is ogg) - their web server needs to be able to identify particular files in order to know how to server them e.g. serve text/html files as simple files, run PHP scripts rather than serve their contents etc. If they haven't got an entry for ogg files, or rather they have and purposely don't allow a binary download, then you'd see exactly this sort of result.
 
Given what you said about paid-for services perhaps the serving of ogg files is one such benefit of such a service.
 
If you can let me/us know the URL we can probably check this for sure.
 
Mathew

---

### Post by pytheas22 on 2008-06-04
Sorry for hating so much on godaddy.  I do think their services are bad and that they do sketchy things, but I guess this isn't the place for criticizing them.  The reason I still use their service is because I don't have the time to build my own server right now or a place to put it; hopefully within a couple months, that will change.

Anyway, I figured out that I can get the file to download normally if I append an extension to its name like .mp3 or .sh.  So I'm guessing that the server looks at the file name extension and then decides how to serve the file, and if it sees .ogg, it won't serve it properly for some reason.  I doubt this is a security setting, because godaddy lets me wget my whole site without a problem, and other files can be downloaded without issue.  I'll get in touch with them and find out what's going on.

I will also send MJN the URL in a private message.

Thanks for the responses.

---

### Post by MJN on 2008-06-05
I had a look at downloading the URL and ran a packet trace to show the HTTP headers however I didn't realise GoDaddy plaster adverts on every page request hence the Content-Type was text (with some Javascript thrown in) as one would expect.

I'm afraid there's nothing you can really do other than use an alternative extension or contact GoDaddy for support.

Mathew

---

### Post by windependence on 2008-06-05
> **pytheas22 said:**
> Sorry for hating so much on godaddy.  I do think their services are bad and that they do sketchy things, but I guess this isn't the place for criticizing them.  The reason I still use their service is because I don't have the time to build my own server right now or a place to put it; hopefully within a couple months, that will change.

Anyway, I figured out that I can get the file to download normally if I append an extension to its name like .mp3 or .sh.  So I'm guessing that the server looks at the file name extension and then decides how to serve the file, and if it sees .ogg, it won't serve it properly for some reason.  I doubt this is a security setting, because godaddy lets me wget my whole site without a problem, and other files can be downloaded without issue.  I'll get in touch with them and find out what's going on.

I will also send MJN the URL in a private message.

Thanks for the responses.

Yes, in fact I am 99% sure there is an Apache setting that tells the server what file extensions can be downloaded via http. try asking them when you call.

-Tim

---

### Post by Dr Small on 2008-06-05
They need to add this to their mime_module:
```
AddType application/ogg .ogg
```

---

### Post by windependence on 2008-06-05
> **Dr Small said:**
> They need to add this to their mime_module:
```
AddType application/ogg .ogg
```

Thanks, I knew there was an Apache setting for this.


-Tim

---

