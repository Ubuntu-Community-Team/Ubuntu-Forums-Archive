---
title: "Tomcat5 on Kubuntu 6.06"
date: 2006-05-31
forum: Server Platforms
---

### Post by wizzkid on 2006-05-31
I am trying to install tomcat5 on kubuntu 6.06. 
I just followed this link:
[https://wiki.ubuntu.com/ApacheMySQLPHP#head-857042915ff2edbb94c9133296e03fb187d10708](https://wiki.ubuntu.com/ApacheMySQLPHP#head-857042915ff2edbb94c9133296e03fb187d10708)
Then it asked me to install the JDK link:
[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

Now its asked me the export JAVA_HOME="path of your java home" ? 

I am wondering where could i check my java home? 

sorry very new to java thing.

Thanks

---

### Post by wizzkid on 2006-05-31
any? :D

---

### Post by dk_pa on 2006-05-31
You could do "locate java" from terminal.

I think java is in /usr/lib somewhere.

---

### Post by wizzkid on 2006-05-31
i tried locate java  even locate jdk, thre are tons of text and when finish, I cannot read all, is there a way to import it to text file?

thanks.

---

### Post by dk_pa on 2006-05-31
You could do...

locate java | more

That should do a page by page listing. 

locate java > yourfile.txt

That would send it to a txt file.

Dig around /usr/lib tho.

---

### Post by wizzkid on 2006-06-01
Thanks boss :)

---

### Post by wizzkid on 2006-06-02
Guys, this really confused me, and I dont know my JAVA_HOME.  Here's the message with I tried to enter sudo /etc/init.d/tomcat5 start

Could not start Tomcat 5 servlet engine because no Java Development Kit
(JDK) was found. Please download and install JDK 1.3 or higher and set
JAVA_HOME in /etc/default/tomcat5 to the JDK's installation directory.

Can you guys help me locate the JAVA_HOME? I've attached my java location.

Thanks and hope you could help me.

---

### Post by wizzkid on 2006-06-03
any? :D

---

### Post by henrikwidth on 2006-06-03
[QUOTE=wizzkid]any? :D[/QUOTE]

Hi

here´s what I did to make it work.

downloaded jdk from sun

chmod +x jdk_something.bin
./jdk_something.bin

this unpacked a folder in my current directory

mv foldername /usr/share/
export JAVA_HOME="/usr/share/foldername/"

I´m sure there are other possible ways of doing this, and I don´t know if /usr/share is the best folder to put it in. but it works for me :)

---

### Post by wizzkid on 2006-06-03
Thanks a lot. I will try this one :D

---

### Post by wizzkid on 2006-06-03
It works! hmm is this safe? heheheh :) 

Thanks

---

### Post by henrikwidth on 2006-06-05
You can also try a more "ubuntuish" way of doing it by enabling multiverse and type: 
*apt-get install sun-java5-jdk*
*export JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun/"*
*export PATH=$PATH:$JAVA_HOME/bin*

Henrik

---

### Post by wizzkid on 2006-06-06
thank a lot :)

i got it :D

---

