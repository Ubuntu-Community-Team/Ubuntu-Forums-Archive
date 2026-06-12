---
title: "Bash Script to read and compute several lines"
date: 2013-02-20
forum: Server Platforms
---

### Post by Valpskott on 2013-02-20
So, I have a file which get a new number added to it every day. And I want to read the 7 last numbers from this file, add them together and then divide by 7 to get an average.

```

week=$(tail -n 7 data.txt)

        while read score
        average=$($average + $score)
        done < $week

average2=$($average / 7)
echo $average2

```

Well, It fails, and google unfortunatly didn't turn up much :/

I get the sense there is a more elegant way of doing this than using loads of variables.

---

### Post by steeldriver on 2013-02-20
How about

```
sum=0
while read val
  do ((sum+=$val))
done < <(tail -7 data.txt)
echo $((sum/7))

```Remember that the shell itself only does integer division - if you want a floating point average you will need to pipe it to bc, I think, e.g.

```
echo "scale = 2; $sum/7" | bc

```

[FYI you should probably count the number of lines that it actually reads and divide by that - rather than assuming tail will return 7 lines]

---

### Post by papibe on 2013-02-21
Hi Valpskott.

If you are not committed to do it purely on bash, here's an alternately solution that uses awk:
```
tail -n 7 data.txt | awk 'BEGIN{sum=0} {sum+=$1} END{print sum/7}'
```  
Regards.

---

### Post by Valpskott on 2013-02-21
Thank you both of you for your suggestions! :)

I went the "non awk" route, even though the awk thing worked, I'm yet to familiarize myself with awk and how it's syntax goes, and I already needed to tweak something.

Marking as solved :)

---

