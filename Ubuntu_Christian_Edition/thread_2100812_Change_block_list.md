---
title: "Change block list"
date: 2013-01-02
forum: Ubuntu Christian Edition
---

### Post by axy_david on 2013-01-02
Ubuntu CE is an OK "mod", save me of all the trouble on installing dansguardian so..
1. Why using chrome and not firefox?
2. How do I configure dansguardian now that there is no GUI so far.
I gotta say that the firewall works nice against proxy sites, but horrible against pornography, for example search something dirty on google images and BAM, not blocked, my opinion is to block images.google.com altogether and tag it as proxy.
Also the blocked keywords needs to be updated.

---

### Post by nixblog on 2013-01-05
> **axy_david said:**
> I gotta say that the firewall works nice against proxy sites, but horrible against pornography, for example search something dirty on google images and BAM, not blocked, my opinion is to block images.google.com altogether and tag it as proxy.
Also the blocked keywords needs to be updated.

Not configured DG for ages but you should be able to enable "safesearch" for Google and other search engines by reviewing and editing,

/etc/dansguardian/lists/bannedregexpurllist

The file is fairly well documented and you can uncomment the entries for "Block unfiltered options on various search engines" so it looks similar to this,

```
######################################################
# Search Engine and Related
######################################################

#Block unfiltered options on various search engines
(^|[\?+=&/])(.*\.google\..*/.*\?.*safe=off)([\?+=&/]|$)
(^|[\?+=&/])(.*\.alltheweb.com/customize\?.*copt_offensive=off)([\?+=&/]|$)

#Block images and video on altavista, alltheweb, yahoo etc - as they are anonomised
#(yahoo.com\/image\/)
#(yimg.com\/image\/)
#(altavista.com\/image\/)
#(altavista.com\/video\/)
#(picsearch.com\/is)

#Block images and video on google
#(images.google)+.*(\.jpg|\.wmv|\.mpg|\.mpeg|\.gif|\.mov) 
#(google.com\/video) #block all video
#(google.com\/ThumbnailServer) #block video thumbnails
#(google.com\/videoplay) #block only playing the video
```

You could also uncomment other options too if you wish. Save the file and restart DG

```
dansguardian -r
```

Hopefully that will force a safe search for Google but, I have found it to be hit or miss on occasions. However you could use another search engine and bypass Google - the only way secure this is to use a blocking list from shalla or urlblocklist, block all search engines  and whitelist Google and force the safe search option.

---

### Post by nixblog on 2013-01-05
Well just tried my own suggestions and it appears not to work :(

Assume Google has probably changed the way they handle searches but, know that safe search works well under Squid/SquidGuard (as used in pfSense). Funny thing is that while I was searching for answers to this, I was blocked viewing several several legit sites by DG - too many false positives was one of the reasons why I stopped using DG before!

---

### Post by axy_david on 2013-01-06
and its so easy to vypass them, just run any webrowser as root and bang....
oh well...it woul've been better if dansguardian and squidproxy were installed as root....
so far I haven't got any flase positives, but I can understan why you were  blocked, after all squidproxy is a proxy

---

### Post by axy_david on 2013-01-13
bump

---

