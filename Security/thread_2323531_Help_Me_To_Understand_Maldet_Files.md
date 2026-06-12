---
title: "Help Me To Understand Maldet Files"
date: 2016-05-06
forum: Security
---

### Post by Sourav_Saha on 2016-05-06
I have installed Maldet from : [http://www.rfxn.com/projects/linux-malware-detect/](http://www.rfxn.com/projects/linux-malware-detect/)


Just curious, what's up with the files in ./maldetect-1.5/files/clean ?
```


[LIST]
[*]base64.inject.unclassed
[*]gzbase64.inject.unclassed
[*]js.inject.VisitorTracker
[*]php.brute.bf1lic
[/LIST]

```

They are also there in Github Repository: [https://github.com/waja/maldetect/tree/master/files/clean](https://github.com/waja/maldetect/tree/master/files/clean)


Are they test files or  cleaning instructions for entire categories of malware?

If they are "test" files why does it only detect one of them? (i.e. "gzbase64.inject.unclassed")


Here is the report I got 


```
FILE HIT LIST:
{HEX}gzbase64.inject.unclassed.15 : /tmp/maldetect-1.5/files/clean/gzbase64.inject.unclassed => /usr/local/maldetect/quarantine/gzbase64.in$
```

---

### Post by Habitual on 2016-05-06
Have you asked [EMAIL="ryan@rfxn.com"]Ryan[/EMAIL]?
Nice post,  but you don't mention updates, if any to maldet...

---

