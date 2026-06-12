---
title: "Problems with bashscript &quot;else&quot;"
date: 2009-06-19
forum: Server Platforms
---

### Post by storskogen on 2009-06-19
I can't get my script to run as i want. It always executes the lines with email.
What have i missed? It should only email me if the IP is changed.

```
#!/bin/bash 
# zddc.sh - Zoneedit.com Dynamic Dns Corrections. 
#Created by Crouse 
#05-15-2007 
#Edit the next 3 lines 
website="x.com" 
zoneeditusername="xxxxxx" 
zoneeditpassword="xxxxxx" 
email=y@x.com

#Update IP address function, corrects settings on zoneedit.com 
updateip () 
{ 
#Change entry for url with the x. prefix 
wget -q -O - --http-user="${zoneeditusername}" --http-passwd="${zoneeditpassword}" "http://dynamic.zoneedit.com/auth/dynamic.html?host=x.${website}" > /dev/null 2>&1 
#Change the entry for the url without the www. prefix 
wget -O  - --http-user="${zoneeditusername}" --http-passwd="${zoneeditpassword}" "http://dynamic.zoneedit.com/auth/dynamic.html?host=${website}" > /dev/null 2>&1 
} 

#Determine the current real ip address for this machine. 
actualip=`lynx -dump -hiddenlinks=ignore -nolist http://checkip.dyndns.org:8245/ | awk '{ print $4 }' | sed '/^$/d; s/^[ ]*//g; s/[ ]*$//g'` 


#Read in the current ip from currentip log file. Assign that value to a variable for comparison. 
currentip=`less /home/$USER/.zoneedit` 

#Output to display .... could echo it all to an email if setup as a cron job. 
echo " " 
echo "Zoneedit.com Update Check" 
echo "The actual IP is: " $actualip 
echo "The current IP is: " $currentip 

if [ "$actualip" == "$currentip" ] ; then 
  echo "The IP's match, nothing to do, exiting." 
  echo " " 
else
  echo "IP's do not match" 
  echo "Updating the zone edit file." ; updateip 
  echo "Updating the .zoneedit file locally." 
  echo $actualip > /home/$USER/.zoneedit 
  echo "ZoneEdit update completed." 
  echo " " 
  [COLOR=Red]echo " " | /usr/sbin/ssmtp $email < .zoneedit[/COLOR]
fi

```

---

### Post by lloyd_b on 2009-06-19
May I suggest changing two of the lines, just for a sanity check:```
echo "The actual IP is: !$actualip!" 
echo "The current IP is: !$currentip!"
```  This will allow you to see if one of them has somehow picked up a trailing space or such that would throw off the match.

I would also suggest changing the use of "less" to extract the line from the .zoneedit file to something that isn't designed for interactive use.  For instance```
currentip=`cat /home/$USER/.zoneedit`
``` or ```
currentip=`head -n 1 /home/$USER/.zoneedit`
```If for no other reason than not all *nix variants will have "less" installed by default, while "cat" and "head" are about as universal as you can get.

Lloyd B.

---

### Post by storskogen on 2009-06-19
I tried changing to your suggestions but it didn't change anything.
The problem isn't the script not running, it is that it doesn't stop when the IP is unchanged since the last check.

I think it is something with:

```
if [ "$actualip" == "$currentip" ] ; then
  echo "The IP's match, nothing to do, exiting." 
  echo " " 
else
  echo "IP's do not match" 
  echo "Updating the zone edit file." ; updateip
  echo "Updating the .zoneedit file locally." 
  echo $actualip > /home/$USER/.zoneedit
  echo "ZoneEdit update completed." 
  echo " " 
  echo " " | /usr/sbin/ssmtp $email < .zoneedit
fi

```

the .zoneedit file is updated and show the right IP and the script says it's the same:

Output if i run it:
```
Zoneedit.com Update Check
The actual IP is: !xxx.xxx.xxx.xxx!
The current IP is: !xxx.xxx.xxx.xxx!
The IP's match, nothing to do, exiting.
```

---

### Post by lloyd_b on 2009-06-20
Just to clarify the issue:  When you run the script, producing the following output:```
Zoneedit.com Update Check
The actual IP is: !xxx.xxx.xxx.xxx!
The current IP is: !xxx.xxx.xxx.xxx!
The IP's match, nothing to do, exiting.
```it is still sending the email?  Am I understanding correctly?

If that's the case, I really don't see how it's happening - the if/then/else/fi structure should preclude that from happening.

I was under the impression (from your original post) that it was taking the "else" clause, even when the IP's matched, which was why I suggested the sanity check on the IP's.

If I'm still misunderstanding the problem (quite possible), then please explain it differently - that often makes it easier to understand.

Lloyd B.

---

