---
title: "Get Webpage Source"
date: 2009-03-31
forum: Server Platforms
---

### Post by Holmes89 on 2009-03-31
I am trying to save a webpage to retrieve data off of it in Ubuntu server. Is this possible? If so how do I do it?

---

### Post by R.Bucky on 2009-03-31
You could do a 
```
wget http://website/webpage.html > /home/username/Dekstop/webpage.html
```

---

### Post by BkkBonanza on 2009-03-31
Except that won't work. wget by default doesn't output to the console so piping won't work. It will store a file with same name as source file. If you want to put it in a different file then use the -O option like this,

wget url -O -     
to output to console, or

wget url -O filename
to put into a file.

---

### Post by hyper_ch on 2009-04-01
try (web)httrack

---

### Post by Holmes89 on 2009-04-01
I got what I wanted but now I was wondering what would be the best way to cut out extra text. I just want to have a program that will go through and extract certain information and then process it. I would prefer to use a script because I want this to be automated. What language should I use and how do I set up an automated task like that?

---

### Post by BkkBonanza on 2009-04-01
Use whatever language you know. Or if you're going to have to learn one then for text extraction a good choice is perl. You can also get the web page in perl easily and output the resulting text. I don't know much perl, so I'd probably write it in php.

You can run the script from a cron (at certain times) or call it from a webpage or startup script. Or wherever you need.

---

