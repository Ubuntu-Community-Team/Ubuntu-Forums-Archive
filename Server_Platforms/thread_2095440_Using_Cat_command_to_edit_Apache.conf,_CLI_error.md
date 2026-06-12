---
title: "Using Cat command to edit Apache.conf, CLI error"
date: 2012-12-16
forum: Server Platforms
---

### Post by whatwasthat on 2012-12-16
Hi there, 
Fairly New to the Linux CLI, so forgive if this is a dumb question... But I cannot find the answer out there.

I am looking to edit the apache.conf file by script from the CLI when I want to add a new Virtual Server record.
In order to do this I am planning on using CAT command inside a .sh shell script like the following:

test.sh file:
```

#bash to use enter #test.sh dirforServer ServerName
echo "Press Ctrl+d to finish" 
cat >> test.txt 
<VirtualHost *:80> 
DocumentRoot "$1" 
ServerName "$2" 
<Directory "$1"> 
allow from all 
Options +Indexes 
</Directory> 
</VirtualHost>

```

Thanks for helping me automate this annoying process.

---

### Post by steeldriver on 2012-12-16
Hi if I'm understanding right you want to use a "here document" in a script? in that case I think you need to use a text label instead of the Ctrl-d that you are using in the interactive shell - something like

```
$ cat **<<EOF** >> test.txt
<VirtualHost *:80>
DocumentRoot "$1"
ServerName "$2"
<Directory "$1">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
**EOF**
$
$ cat test.txt
<VirtualHost *:80>
DocumentRoot ""
ServerName ""
<Directory "">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
$

```I've used 'EOF' as the label here, but afaik it can be any unambiguous textual label - you could use 'END' for example

see [http://tldp.org/LDP/abs/html/here-docs.html](http://tldp.org/LDP/abs/html/here-docs.html)

Hope this helps

---

### Post by whatwasthat on 2012-12-16
Thanks for the tips, here is what I have go that is working for me
```

bin/bash
# Another 'cat' here document, using parameter substitution.

# Try it with no command-line parameters,   ./scriptname
# Try it with one command-line parameter,   ./scriptname Mortimer
# Try it with one two-word quoted command-line parameter,
#                           ./scriptname "Mortimer Jones"

CMDLINEPARAM=1     #  Expect at least command-line parameter.
if [ $# -ge $CMDLINEPARAM ]
then
        vDIR=$1
        vSVR=$2
else
        vDIR="/www/var/client_sites/"
        vSVR="xxx.x"
fi
cat >> /etc/apache2/apache2.conf <<EndofScript
<VirtualHost *:80>
DocumentRoot "$vDIR"
ServerName "$vSVR"
<Directory "$vDIR">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
<VirtualHost *:80>
DocumentRoot "$vDIR"
ServerName "www.$vSVR"
<Directory "$vDIR">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
EndofScript

```

---

