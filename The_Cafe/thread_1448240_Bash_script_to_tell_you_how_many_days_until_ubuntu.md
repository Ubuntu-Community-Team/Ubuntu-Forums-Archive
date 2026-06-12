---
title: "Bash script to tell you how many days until ubuntu X is released"
date: 2010-04-06
forum: The Cafe
---

### Post by alex_o on 2010-04-06
i have made a small bash script which assumes that ubuntu is released on the last day of April and October, it then works out the date and finds the difference and tells you if it will be LTS!!!
```
#!/bin/bash
days(){
[ "$#" == "2" ] && date -d "$1/01/$2 +1month -1day" +%d
[ "$#" == "1" ] && days $1 `date +%Y`
[ "$#" == "0" ] && days `date +%m%Y`
}
month(){
total=0
month=`date +%m`
while [ $month -le $1 ];do
total=$((`days $month` + $total))
month=$(($month+1))
done
total=$(($total - `date +%d`))
echo $total
}
mnth=`date +%m`
LTS=0
if [ $mnth -ge 05 ];then
	LTS=0
else
	LTS=1
fi
if [ $mnth -ge 11 ];then
	LTS=1
fi
if [ $LTS = 1 ];then
	if [ $mnth -lt 11 ];then
		echo "ubuntu `date +%y`.04LTS available in `month 4` days"
	else
		echo "ubuntu `date +%y`.04LTS available in $((`month 12`+`month 4`)) days"
	fi
else
	echo "ubuntu `date +%y`.10 available in `month 10` days"
fi
```

* function: days is not my code, i copied and pasted it :lolflag:

~enjoy~) :P

---

