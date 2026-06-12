---
title: "Snort as Anamoly Based IDS"
date: 2009-03-31
forum: Security
---

### Post by bilal_jan on 2009-03-31
Hello everyone
I am doing my final year project in wh i have to configure snort to work as an anamoly based IDS for wireless Ad-hoc networks.
I am struck at a point and i cant go further unless i solved this problem.
The qurey is that i have made snort to log packets to sql server and i want to use "statistical anomaly detection technique" in which i have to draw a baseline behaviour and traffic that deviats from this normal behaiour will be declared as anamoly.
i am struck with this i dont know how to begin with.i am using SNORT IDS to track anamolies.
can anyoe please tell me how to use SNORT to work like this.
if u do have anyother suggestion please do give that to me as well.
[B]Best regards
Ahmed Bilal Jan[/B]

---

### Post by bodhi.zazen on 2009-03-31
Sounds like you will have to do some sort of statistical analysis of the data snort is logging, determine what is "normal", and then detect deviation from normal :)

No, snort will not do this for you.

Good luck , but please be aware we do not support home work here, you are expected to do you own work, by your teachers and by us as well.

---

