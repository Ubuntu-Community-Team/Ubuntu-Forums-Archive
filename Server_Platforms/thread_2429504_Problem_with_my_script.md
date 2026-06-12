---
title: "Problem with my script"
date: 2019-10-19
forum: Server Platforms
---

### Post by secooonder on 2019-10-19
[FONT=Helvetica]Hi,
[/FONT]
[FONT=Helvetica]i want to write script about a file(trial.txt).

my trial.txt;

[COLOR=#333333][FONT=&amp] 
[/FONT][/COLOR]
[/FONT]
>  izlemachd.com
 sonmodamodelleri.com
 dizimagazin.net
 zeytinoyun.com
 asoyun.net
 magazincafe.com
 gameofglam.com



[FONT=Helvetica]The output i wanted is ;[/FONT]
[FONT=Helvetica]> 

[COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]izlemachd[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.com$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sonmodamodelleri[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.com$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]dizimagazin[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.net$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]zeytinoyun[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.com$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)asoyun\.net$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]magazincafe[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.com$
[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp](^|\.)[/FONT][/COLOR][COLOR=#333333][FONT=&amp]gameofglam[/FONT][/COLOR][COLOR=#532BA8][FONT=&amp]\.com$[/FONT][/COLOR]
My script ;
more run.sh
**> #!/bin/bash**
**> input="trial.txt"**
**> while IFS= read -r line**
**> do**
**> echo "(^|\.)${line//./\.}$"**
**> done < "$input"**[/FONT]
[FONT=Helvetica]i run " ba*sh run.sh> /root/abc.list"*[/FONT]
[FONT=Helvetica]*My* output file is;[/FONT]
> 
[COLOR=teal]$^[/COLOR]|\.)izlemachd\.com
[COLOR=teal]$^[/COLOR]|\.)sonmodamodelleri\.com
[COLOR=teal]$^[/COLOR]|\.)dizimagazin\.net
[COLOR=teal]$^[/COLOR]|\.)zeytinoyun\.com
[COLOR=teal]$^[/COLOR]|\.)asoyun\.net
[COLOR=teal]$^[/COLOR]|\.)magazincafe\.com
[COLOR=teal]$^[/COLOR]|\.)gameofglam\.com



[FONT=Helvetica]1)there should be no dollar signs at the beginning of the line .[/FONT]
[FONT=Helvetica]there must be a dollar sign at the end of the line.[/FONT]
[FONT=Helvetica]2)there sholud be a parentheses sign at the early of the line .[/FONT]
[FONT=Helvetica]

what&#8217;s wrong in my script ?[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I spent a lot of time on this but I couldn&#8217;t solve it.Please help me

Thank you very much for your help[/FONT]

---

### Post by Doug S on 2019-10-19
Very interesting. I am not a bash expert, but I tried it to see if I could help.
Your script, as listed, works fine for me:

```
doug@DOUG-64:~/temp5$ cat trial.txt
izlemachd.com
sonmodamodelleri.com
dizimagazin.net
zeytinoyun.com
asoyun.net
magazincafe.com
gameofglam.com
doug@DOUG-64:~/temp5$

``````
doug@DOUG-64:~/temp5$ cat script
#!/bin/bash
input="trial.txt"
while IFS= read -r line
do
echo "(^|\.)${line//./\.}$"
done < "$input"

``````
doug@DOUG-64:~/temp5$ ./script
(^|\.)izlemachd.com$
(^|\.)sonmodamodelleri.com$
(^|\.)dizimagazin.net$
(^|\.)zeytinoyun.com$
(^|\.)asoyun.net$
(^|\.)magazincafe.com$
(^|\.)gameofglam.com$

```also checked redirected output:```
doug@DOUG-64:~/temp5$ ./script >output.txt
doug@DOUG-64:~/temp5$ cat output.txt
(^|\.)izlemachd.com$
(^|\.)sonmodamodelleri.com$
(^|\.)dizimagazin.net$
(^|\.)zeytinoyun.com$
(^|\.)asoyun.net$
(^|\.)magazincafe.com$
(^|\.)gameofglam.com$

```The computer is a server:```
doug@DOUG-64:~/temp5$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

```

---

### Post by secooonder on 2019-10-20
Doug S.
Thank you.
i tried " [COLOR=#000000][FONT=&quot]./script >output.txt"
The problem is solved.

Thank you very much for your help[/FONT][/COLOR]

---

