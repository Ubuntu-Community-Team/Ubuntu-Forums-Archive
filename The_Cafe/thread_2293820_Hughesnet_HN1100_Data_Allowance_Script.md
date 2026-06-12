---
title: "Hughesnet HN1100 Data Allowance Script"
date: 2015-09-07
forum: The Cafe
---

### Post by brian-mccumber on 2015-09-07
I recently switched to Ubuntu and my ISP is Hughesnet and I couldn't find a status meter for Ubuntu or a script that would work to display the data limit status for my service plan. The few scripts I found for this were overly complicated and parsed unnecessary data and they did not work when I tried them. I just wanted a simple way to see how many gigs I have left without having to open the browser and navigate to the control center so I wrote this bash script which is actually the first shell script I have written other than hello world and echoing some text with a loop. 

Let me tell you, I have been writing c, php, javascript, and basic for many years now and bash scripting is a completely different animal but looks so similar to c and php that I was seriously having problems. I had to do alot of searching in order to get this script to run right but it was a good introduction to the 'joy' of bash scripting. Anyway, it's a good quick tool for checking how much data I have left to consume for the month. I didn't bother converting the output to a percentage like the control center and status meter does because 4.5gb is easier to read than 45% of 10gb. I checked the output against the control center and a roommate's status meter they run on Windows and it is accurate. I am pretty sure it will work with different Hughesnet modems other than the HN1100 that I use because I found the path to the data on the modem from someone who was trying to write a python widget for this same thing for a different modem model. If someone else can get some use out of it that's great. I just keep it in /home so when I hot key the terminal up I can type a couple chars and hit tab and see what I have left.

[ATTACH=CONFIG]264314[/ATTACH]

```

#!/bin/bash


#Queries Hughesnet HN1100 modem for usage allowance information
#Parses the info and displays the relevent information


info=$(curl -silent http://www.systemcontrolcenter.com/getdeviceinfo/info.bin | grep -e ^Any -e ^Bonus)


index=0


for word in $info
do
    amt="$(echo $word | tr -cd [:digit:]'\n')"
    mb[index]=$(echo "scale=2; $amt/1000" | bc)
    ((++index))
done


echo -e "\n\nAnytime data usage is from 8am - 2am"
echo "-------------------------------------"
echo "Anytime Data Allowance: "${mb[1]}"GB"
echo "Anytime Data Remaining: "${mb[0]}"GB"
echo "====================================="
echo "Bonus bytes usage is from 2am - 8am"
echo "-------------------------------------"
echo "Bonus Bytes Allowance: "${mb[3]}"GB"
echo -e "Bonus Bytes Remaining: "${mb[2]}"GB"


tt=$(curl -silent http://www.systemcontrolcenter.com/getdeviceinfo/info.bin | grep -e ^User -e ^TimeLeft)


index1=0


for word1 in $tt
do
    amt="$(echo $word1 | tr -cd [:digit:]'\n')"
    tito[index1]=$amt
    ((++index1))
done
time=$(echo "scale=0; (${tito[0]}/60)/24" | bc)
token=$(echo "scale=2; ${tito[1]}/1000" | bc)
echo "====================================="
echo "Token Bytes Available: "$token
echo -e "Days Until Refill: "$time'\n\n'


read -p "Press any key to close... " -n1 -s

```

---

### Post by brian-mccumber on 2015-09-10
I created a desktop launcher for the script and added a pause to the script so it can be viewed when ran from the launcher otherwise the terminal opens and shuts to quickly to read anything. I made a 64x64 icon for it using part of the Hughesnet logo.

[ATTACH=CONFIG]264343[/ATTACH]

[ATTACH=CONFIG]264341[/ATTACH]

modStats.desktop
```

[Desktop Entry]
Version=1.1
Name=modStat
Comment=Check modem data resources
Exec=/usr/bin/modStat
Icon=/home/yomama/.icons/HughesNet_logo.png
Terminal=true
Type=Application
Categories=Utility;Application;
Name[en_US]=Hughesnet Status

```

---

