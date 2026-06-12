---
title: "Iptables file parser"
date: 2015-03-05
forum: Security
---

### Post by rodrigo19 on 2015-03-05
Hi community, I've been working on a script that check if an iptables file has erros, in case the script has errors, the script will tell you where the error is.

I know that you have iptables-save and iptables-restore, but if you are like me that you have many iptables files for differents customers, with comments and change request numbers in it. You may want to check that specific file, and not a auto generated file.

I would like to share this, and if anyone want to help me to improve this, very welcome to it.
Please be nice! :)

```

#! /bin/bash
## Autor   : Rodrigo Tumaian - rodrigo.tumaian (AT_N0_SP4m) gmail
## Ano     : Marzo 2015
## Version : 1.0
## GPLv3 
##
####
## I had to give something back to the community from where I have learned so much.
####
##
############################################## Some considerations #################################
### This software comes with no guarantee
###
### This script was made using OpenSuse and Ubuntu, for all my iptables files.
### In all my test this script worked very well, maybe in other GNU/Linux distribution it doesn't.
###
### Please send me any kind of bug you find, or any collaboration to improve this script.
###
### This script does not support the use of &#8220;while&#8221; but can be easily adapted to make it work.
###
############################################## IMPORTAN #############################################
## Please run this script using nohup, you don&#8217;t wanna run iptables -F while you are using ssh :P  ##
## Example: nohup ./test_filler > test_filter.out
## To check where the errors are in a easy way: grep Error test_filter.out
##




PATH_GRL=/etc
PATH_FILTER=$PATH_GRL/iptables-filters
LOOP_TMP=$PATH_GRL/.bucle
VARIABLES=$PATH_GRL/.variables
RUN_BLOCK=0
LINE_COUNTER=0;
CANT_FOR=0;



## I do this crazy thing, because I wanna make sure that the file is empty
## This is the easy solution


touch $LOOP_TMP
rm -f $LOOP_TMP
touch $LOOP_TMP
chmod +x $LOOP_TMP
touch $VARIABLES
rm -f $VARIABLES
touch $VARIABLES
chmod +x $VARIABLES



GET_IN_LOOP=0
##
## Here I find the vars in the filter file and try define them as global to make this work&#8230; I&#8217;m quite sure that must be a better solution
## Can we improve this?


for VAR in `grep \= $PATH_FILTER | grep -v ^# | grep -v LOG`; do
        echo "export $VAR" >> $VARIABLES
done;
source $VARIABLES




while read LINEA; do
        let LINE_COUNTER=$LINE_COUNTER+1;
        # Avoid all the comments with this
        if [ -z "`echo "$LINEA" | grep ^#`" ]; then
                #find the &#8220;for &#8220; and send them to a file
                if [ -n "`echo "$LINEA" | grep "for "`" ]; then
                        GET_IN_LOOP=1
                        let CANT_FOR=$CANT_FOR+1;
                        echo "$LINEA" >> $LOOP_TMP
                fi;
                if (($GET_IN_LOOP)) && [ -n "`echo "$LINEA" | grep -v "for "`" ] && [ -n "`echo "$LINEA" | grep -v done`" ]; then
                        echo "$LINEA" >> $LOOP_TMP
                fi;
                if (($GET_IN_LOOP)) && [ -n "`echo "$LINEA" | grep done`" ]; then
                        echo "$LINEA" >> $LOOP_TMP
                        DONE=1;
                        let CANT_FOR=$CANT_FOR-1;


                fi
                if [ "$CANT_FOR" = "0" ] && (($DONE)); then
                        GET_IN_LOOP=0
                        RUN_BLOCK=1
                fi;
                ## when the for is done, I run the code
                if (($RUN_BLOCK)); then
                        echo
                        echo &#8220;We are going to run this code: "
                        cat $LOOP_TMP
                        $LOOP_TMP


                        if [ "$?" != "0" ]; then
                                echo "------------------------------------------------"
                                echo
                                echo "Error en Linea: $LINE_COUNTER"
                                echo "Linea: $LINEA"
                                echo
                                echo "------------------------------------------------"
                        fi;
                        GET_IN_LOOP=0
                        RUN_BLOCK=0;
                        rm -f $LOOP_TMP
                        touch $LOOP_TMP
                        chmod +x $LOOP_TMP
                fi;
                if ! (($RUN_BLOCK)) && ! (($GET_IN_LOOP)) && ! (($DONE)); then
                        eval $LINEA
                        if [ "$?" != "0" ]; then
                                echo "------------------------------------------------"
                                echo
                                echo "Error en Linea: $LINE_COUNTER"
                                echo "Linea: $LINEA"
                                echo
                                echo "------------------------------------------------"
                        fi;


                fi;

                # I don't remember why I added this :P
                if [ "$?" != "0" ] && ! (($GET_IN_LOOP)) && ! (($DONE)); then
                        echo "------------------------------------------------"
                        echo
                        echo "Error en Linea: $LINE_COUNTER"
                        echo "Linea: $LINEA"
                        echo
                        echo "------------------------------------------------"
                fi;
                if (($DONE)); then
                        DONE=0;
                fi;
        fi;




done < $PATH_FILTER;


```

Hope this could be useful for somebody.

Kindly Regards,
Rodrigo

---

### Post by Doug S on 2015-03-08
Hi and welcome to Ubuntu forums,

I had a look at your script, thanks for sharing it. 
I can not figure it out well enough to be confident in trying to run it. And I will not run it without knowing exactly what it does.
I am leery when script creates hidden files in the /etc directory, and has comments like "# Some weird situation, I don’t remember right now", and  "Please run this script using nohup".

---

### Post by rodrigo19 on 2015-03-09
> **Doug S said:**
> Hi and welcome to Ubuntu forums,

I had a look at your script, thanks for sharing it. 
I can not figure it out well enough to be confident in trying to run it. And I will not run it without knowing exactly what it does.
I am leery when script creates hidden files in the /etc directory, and has comments like "# Some weird situation, I don’t remember right now", and  "Please run this script using nohup".

Hi Doug S, thanks for watching this post.

I will try to answer all of your questions:

> **Doug S said:**
> I can not figure it out well enough to be confident in trying to run it.

Well the script reads every line in an iptables file, when he finds and errors, he will tell you where the error is.

I'll give you an example:

```

iptables -F
iptables -X
iptables -Z
iptables -t nat -F
iptables -t nat -X
iptables -t nat -Z
iptables -t mangle -F
iptables -t mangle -X
iptables -t mangle -Z


iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

## Some input rules
iptables -A INPUT -p tcp -s [172.16.0.0/16]("http://192.168.0.0/16")  --dport 22 -m conntrack --ctstate  NEW -j ACCEPT
iptables -A INPUT -p tcp -s [10.11.16.0/24]("http://10.220.5.0/24")  --dport 22 -m conntrack --ctstate  NEW -j ACCEPT
iptables -A INPUT -p tcp -s [172.16.32.0/23]("http://192.168.32.0/23")  --dport 53 -m conntrack --ctstate  NEW -j ACCEPT
iptables -A INPUT -p udp -s [172.16.32.0/23]("http://192.168.32.0/23")  --dport 53 -m conntrack  --ctstate  NEW -j ACCEPT
iptables -A INPUT -p udp -s [172.16.35.0/24]("http://192.168.35.0/24")  --dport 53 -m conntrack --ctstate  NEW -j ACCEPT
iptables -A INPUT -p tcp -s [172.16.35.0/24]("http://192.168.35.0/24")  --dport 53 -m conntrack --ctstate  NEW -j ACCEPT

## Some coments
iptables -A FORWARD -s 172.16.33.165 -d 172.16.35.16 -p tcp -dport 3389 -j ACCEPT
iptables -A FORWARD -s 172.16.33.165 -d 172.16.35.17 -p tcp --dport 3389 -j ACCEPT
```

This could be any iptables file. This file has an error. These are just a couple of lines, so is not going to be hard to find the error. The problems is when this file has like 3000 lines or so... it is going to be very hard to find all the errors in the file, that is way I made this script.

By running this script he will run all the lines, one by one, and after that, the script will check the [`$?`]("http://stackoverflow.com/questions/5163144/what-are-the-special-dollar-sign-shell-variables?answertab=votes#tab-top") value to see if the las line has an error, you could find this in:
```
"[COLOR=#000000][FONT=Ubuntu Mono] if [ "$?" != "0" ]; then"[/FONT][/COLOR]
```

---

> **Doug S said:**
> [COLOR=#000000]I am leery when script creates hidden files in the /etc directory,[/COLOR]

You can change the directory if you wanted, in fact, I do not run this script in /etc directory.. but since /etc it's where the configuration files are, I thought that this directory could be a better options.
The hidden files are these:

**.bucle** - This file appear when you have a for structure in your iptables files. The for will go inside this file.
When the script finds the "done" in the "for" he will run the file .bucle
**.variables** - The script will find al the vars definded in the script, and will put it inside this file.
**.errores** - It is not necessary this file anymore, this was for my first version.. now that I'm checking this is not necessary. (Thanks, this is the first thing to improve)

> **Doug S said:**
> [COLOR=#000000]"# Some weird situation, I don’t remember right now"[/COLOR]

Just a joke.

> **Doug S said:**
>  [COLOR=#000000]"Please run this script using nohup".[/COLOR]

This is very important, if you run this script without using nohup while you are using a remote conection, when you run "iptables -F" you will lose the connection.
The worst part, is that the script will hang, and you will have to have physical access to the machine, to get the connection back.

If you are not sure about this script and you still want to test it, try to run it in a VM. All my test started in a VM, and then I decided to use this script in a production environment.

I could tell you, this script works for all my machines.

Hope This was helpful. If you have any questions do not hesitate to write me :)

Regards,
Rodrigo

---

