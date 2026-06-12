---
title: "Crontab command fails but .sh file appears to run"
date: 2011-10-18
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-10-18
Have reinstalled Ubuntu Server 11.04 and have the following crontab command```
MAILTO me@mydomain.com
*/5 * * * * /var/data/bin/zoneedit.sh
```The content of zoneedit.sh is```
#!/bin/bash

ipfile='/var/data/bin/ipaddress'

[[ -f "$ipfile" ]] && ipold="$(< "$ipfile" )"

ipnew="$( wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //;s/<.*$//' )"

if [[ "$ipold" != "$ipnew" ]]; then

  echo "$ipnew" > "$ipfile"

  /usr/sbin/ssmtp me@mydomain.com < /var/www/ipaddress

  wget -O - --http-user=Me --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'

  wget -O - --http-user=Me --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=mydomain.com'

fi
```As far as I know, the code is exactly as was before reinstalling. The file /var/data/bin/ipaddress exists and even if IP address in the file is the current external IP address it still fails, so the error is not in the second half of the program.

The ownership of the folder/files etc is mine.

The error message emailed is```
/bin/sh: /var/data/bin/zoneedit.sh: not found
```Just to clarify, the following code with correct details from the second half of the .sh file executes as expected.```
wget -O - --http-user=Me --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'

wget -O - --http-user=Me --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=mydomain.com'
```

if you try to run```
/var/data/bin/zoneedit.sh
```from the terminal, the error is```
bash: /var/data/bin/zoneedit.sh: //bin/bash^M: bad interpreter: No such file or directory
```The comments in the thread title concerning running the file is related to directly executing the file in the folder /var/data/bin/

---

### Post by Azdour on 2011-10-18
Hi,

It looks like you may have a special character in your shell script. By any chance did you create the script on Windows?

I believe you may be able to see the special character through vi, or there is a dos2unix application you might want to use.

---

### Post by matt_symes on 2011-10-18
Hi

Yep. This is due to Windows CR/LF endings by the looks of it. Open in gedit, save as and change the line endings Linux/Unix. That's an easy way to change in 10.04 at least.

Or you can use sed.

```
sed -i 's/\r//' /path/to/file.sh
```Kind regards

---

### Post by ChrisRChamberlain on 2011-10-18
Thanks both for your replies.

dos2unix did the job, the file had been restored from a Windows backup so the problem was self inflicted.

---

