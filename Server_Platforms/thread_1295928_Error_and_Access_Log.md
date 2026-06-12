---
title: "Error and Access Log"
date: 2009-10-20
forum: Server Platforms
---

### Post by Archngel on 2009-10-20
Hi, Im not sure if Im posting in the right tread but here it goes for a simple question.

First: Is there a way to extract the error log of an ubuntu web server by date frame ie( from 100109 to 101509 ) rather than extracting the entire log from the begening of time to present day?
If yes can someone write me the command or how to get it. 

Second: can we do the same procedure for the access log, in order to see what is going on on the server on specific date frame. 

I have been chosen to review logs of our server, but the one that is extracting them is sending me file ( error log ) 160mg in size containing data as far back as the server has been up, in 2007. no needt say that regular text editor are crunched by the size, and if I go with write or winword, it exceeded their limits of nearly 35000 pages. Similar thing for the access log.

Id like to tell the guy on how to do it proprely

Thx in advance for any help you can provide on this mather.

Regards to all

Arch

---

### Post by Archngel on 2009-10-20
Hi, this might be more suited for this cathegory here it goes for 2 simple questions.

First: Is there a way to extract the error log of an ubuntu web server by date frame ie( from 100109 to 101509 ) rather than extracting the entire log from the begening of time to present day?
If yes can someone write me the command or how to get it. 

Second: can we do the same procedure for the access log, in order to see what is going on on the server on specific date frame. 

I have been chosen to review logs of our server, but the one that is extracting them is sending me file ( error log ) 160mg in size containing data as far back as the server has been up, in 2007. no needt say that regular text editor are crunched by the size, and if I go with write or winword, it exceeded their limits of nearly 35000 pages. Similar thing for the access log.

Id like to tell the guy on how to do it proprely

Thx in advance for any help you can provide on this mather.

Regards to all

Arch

---

### Post by Lars Noodén on 2009-10-20
If you prefer sql:

Well, in the future, you can add (in addition to the existing logs) an export to one of the SQL databases available in  Ubuntu.

Retroactively, you might try [asql](http://www.steve.org.uk/Software/asql/).



Otherwise, 

You can write a script in perl or python to read the log files and extract the records you want and store them in a separate BerkelyDB, SQLite, GT.M, MySQL or Postgresql database.

I'm not so keen on the default custom log format in apache, since it requires a little bit of pattern matching to get at the data.  

```

# old format : 
#  LogFormat "%h %l %u %t \"%r\" %>s %b" common

# new easier to parse, tab-delimited format :
LogFormat "%h\t%l\t%u\t%t\t\"%r\"\t%>s\t%b" common

```

---

### Post by Archngel on 2009-10-20
Hi everyone,

I guess this is the right room for this since its regarding Ubuntu Server. 

Can someone tell me if its possible to:

First: extract the error log of an ubuntu web server by date frame ie( from 100109 to 101509 ) rather than extracting the entire log from the begening of time to present day?
If yes can someone write me the command or how to get it. 

Second: can we do the same procedure for the access log, in order to see what is going on on the server on specific date frame. 

On this server, there is no interface ( GUI ) and I dont have physical access to it. Im just sent the log in a file.

I have been chosen to review logs of our server, but the one that is extracting them is sending me file ( error log ) 160mg in size containing data as far back as the server has been up, in 2007. no need to say that regular text editor are crunched by the size, and if I go with write or winword, it exceeded their limits of nearly 35000 pages. Similar thing for the access log.

Id like to tell the guy on how to do it proprely so that he or I can go get it myself just what I need.

Thx in advance for any help you can provide on this mather.

Regards to all

Arch

---

### Post by Elfy on 2009-10-20
Closed duplicate - [http://ubuntuforums.org/showthread.php?t=1295931](http://ubuntuforums.org/showthread.php?t=1295931)

---

### Post by Elfy on 2009-10-20
Threads merged, please do not post duplicates.

---

### Post by Archngel on 2009-10-21
Thx Will look into it. 

Regards

Arch

---

### Post by Archngel on 2009-10-21
Sorry ForestPixie, Just realized that I wasnt getting any reply on my first post because in the wrong section, you can delete what ever is not pertinent.

Regards

Arch

---

### Post by i.r.id10t on 2009-10-21
1) Start rotating your logs on a regular basis.

2) For the old stuff, you can use grep to find the dates and just direct the output to a new file.

---

