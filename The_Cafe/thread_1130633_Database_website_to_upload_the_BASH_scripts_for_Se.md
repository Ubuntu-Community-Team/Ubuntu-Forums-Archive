---
title: "Database/ website to upload the BASH scripts for Servers/Desktops"
date: 2009-04-20
forum: The Cafe
---

### Post by patrick295767 on 2009-04-20
Hello, 

You have an outstanding Uptime, you run a server, you are use crontab, ... or you use daily scripts for your Desktop for your work... 

So a Database/ website to upload dedicated to BASH scripts for Servers/Desktops, could be good to have that!?
 Where can I upload my scripts?
  
An example, this upload the weather for your website:
first, cd ; mkdir -p tmp/updateonofflinesh
uploadonweather.sh```

#!/bin/sh
cd
userz=`cat .uploadonwebsite  | grep user  | head -n 1 | cut -d' ' -f3`
passz=`cat .uploadonwebsite  | grep pass  | head -n 1 | cut -d' ' -f3`
foldertoupload=`cat .uploadonwebsite  | grep location2  | head -n 1 | cut -d' ' -f3`
hostz=`cat .uploadonwebsite  | grep host  | head -n 1 | cut -d' ' -f3`
filestoretrieve=`cat .uploadonwebsite  | grep location1  | head -n 1 | cut -d' ' -f3`
cd ; cd tmp/updateonofflinesh
rm weatherstatus.html
echo "Getting from the net ..."
echo " "
#  add below in XXURCODEHERECOUNTRY  your code country
weatherget  -s XXURCODEHERECOUNTRY --metric  --extended-day=5 > weatherstatus.tmp
echo "Local temperature, Today, `date +%A' '%D`: " > weatherstatus.html
cat weatherstatus.tmp | grep Temperature >> weatherstatus.html
echo "<br>" >> weatherstatus.html
echo "  -  " >> weatherstatus.html
cat weatherstatus.tmp | grep Conditi  | grep Condition | head -n 1  >> weatherstatus.html
echo "  and  " >> weatherstatus.html
cat weatherstatus.tmp | grep UV >> weatherstatus.html
echo "<br>" >> weatherstatus.html
echo "Local temperature, Coming days: " >> weatherstatus.html
echo "<br>" >> weatherstatus.html
echo "  -  " >> weatherstatus.html
cat weatherstatus.tmp | grep -v ":" | tail -n 10    >> weatherstatus.html
echo "<br>" >> weatherstatus.html
echo "  -  " >> weatherstatus.html
cat weatherstatus.tmp | grep High | sed  's/High/-/g' | tail -n 5 >> weatherstatus.html
echo " (High)" >> weatherstatus.html
echo "<br>" >> weatherstatus.html
echo "  -  " >> weatherstatus.html
cat weatherstatus.tmp | grep Conditi  | grep Condition | sed  's/Conditions/-/g' | tail -n 5  >> weatherstatus.html
echo "<br>" >> weatherstatus.html
cat weatherstatus.html
echo "Uploading..."
ls -la weatherstatus.html
wput -u  weatherstatus.html ftp://$userz:$passz@$hostz/$foldertoupload
```
does sthg like on your site:
> Local temperature, Today, Sunday 04/19/09: Temperature : 14 C
- Conditions : Fair and UV : Low, 0
Local temperature, Coming days:
- Tonight Monday Tuesday Wednesday Thursday
- - : N/A C - : 21 C - : 20 C - : 19 C - : 15 C (High)
- - : Partly Cloudy - : Partly Cloudy - : Mostly Sunny - : Mostly Sunny - : Light Rain 

 - 
 - 
**So the question, where can we share our useful/un-useful scripts (shell/BASH scripts) ?**
 - 
 -

---

### Post by cariboo on 2009-04-20
Have a look at [Hot Scripts]("http:///www.hotscripts.com/").

Jim

---

### Post by patrick295767 on 2009-04-20
> **cariboo907 said:**
> Have a look at [Hot Scripts]("http:///www.hotscripts.com/").

Jim

Nope, no BASH for LINUX

---

