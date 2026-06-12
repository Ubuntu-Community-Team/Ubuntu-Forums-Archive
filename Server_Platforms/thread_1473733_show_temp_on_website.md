---
title: "show temp on website"
date: 2010-05-05
forum: Server Platforms
---

### Post by Gompa on 2010-05-05
iam trying to show cpu temp on my website but i have no idea how to start with this.

i tryed to make a symlink to
 /proc/acpi/thermal_zone/TZ00/temperature

but i have no clue if what iam doing is even acomplised like this

could some one please help me to show the cpu temp via php

---

### Post by cdenley on 2010-05-05
You could probably just do this:
[PHP]
<?php
print file_get_contents('/proc/acpi/thermal_zone/TZ00/temperature');
?>
[/PHP]
but my path is a little different, so you might want to make it work regardless of the directory name "TZ00", and perhaps add some error detection.
[PHP]
<?php
print getCpuTemp()."\n";

function getCpuTemp() {
        $temp=@scandir('/proc/acpi/thermal_zone');
        if(!$temp)
                return 'N/A';
        foreach($temp as $d) {
                $path='/proc/acpi/thermal_zone/'.$d.'/temperature';
                if(is_file($path))
                        return trim(file_get_contents($path));
        }
        return 'N/A';
}
?>
[/PHP]

---

### Post by Gompa on 2010-05-05
thanks for your reply

i tryed this:
<?php
print file_get_contents('/proc/acpi/thermal_zone/TZ00/temperature');?> 

but i just get a empty page ?
just as with the symlink

---

### Post by cdenley on 2010-05-05
Can you get the temperature at all?
```

cat /proc/acpi/thermal_zone/TZ00/temperature

```

---

### Post by Gompa on 2010-05-05
yeah that does work
this is the output:


$ cat /proc/acpi/thermal_zone/TZ00/temperature
temperature:  43 C


i can also cat the symlink (if that mathers)

---

### Post by cdenley on 2010-05-05
```

ls -l /proc/acpi/thermal_zone/TZ00/temperature
echo "<?php print file_get_contents('/proc/acpi/thermal_zone/TZ00/temperature');?>"|sudo tee /var/www/cputemp.php
sudo chmod 644 /var/www/cputemp.php
sudo apt-get install php5-cli
php /var/www/cputemp.php
echo -e "GET /cputemp.php HTTP/1.0\n"|nc 127.0.0.1 80
tail /var/log/apache2/access.log
tail /var/log/apache2/error.log

```

---

### Post by Gompa on 2010-05-05
after i tryed : 
```
ls -l /proc/acpi/thermal_zone/TZ00/temperature
echo "<?php print file_get_contents('/proc/acpi/thermal_zone/TZ00/temperature');?>"|sudo tee /var/www/cputemp.php
sudo chmod 644 /var/www/cputemp.php

```
it worked :) i have no clue what i did wrong and i dont really understand what happened just for my clarification 

```
ls -l /proc/acpi/thermal_zone/TZ00/temperature
```  ^shows the file permissions

```
echo "<?php print file_get_contents('/proc/acpi/thermal_zone/TZ00/temperature');?>"|sudo tee /var/www/cputemp.php
```about this part iam unsure it pasts the part of the code you commented earlier in to a file called cputemp.php
right ?


thanks a lot for your help :)

---

### Post by Gompa on 2010-05-05
can someone please explain to me how to let php execute a command like df for disk information or a easy way to output commands into a readable file
i tried```
echo exec('whoami');
```
but it didn't work and i dont know how to enable it

ah it was php savemode that prohibited me from executing scripts

---

### Post by cdenley on 2010-05-05
Also, "exec" only returns the last line of output. You probably want "shell_exec".
[http://us3.php.net/manual/en/ref.exec.php](http://us3.php.net/manual/en/ref.exec.php)

---

