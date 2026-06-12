---
title: "PHP CLI to run forever"
date: 2010-03-27
forum: Server Platforms
---

### Post by Creek on 2010-03-27
Hello,

I've got a php script that runs in a while(true) loop and I want this script to run until I stop it manually, which can be a day, two weeks or five months.

However, my php script breaks for some reason, and it's not the while loop.
The script is using sockets (with fread()) if that is to any help.

I don't use the cli very often, so my question is if there are any limits in the cli config that can cause this.

The script alone is correct (stream_set_timeout for the socket, and set_time_limit for the execution time), so I figured that it must be in the cli.

Any help is appreciated.

---

### Post by ken22 on 2010-03-27
when it breaks, does it dump/print anything?

---

### Post by ken22 on 2010-03-27
php cli shouldn't be affected by max execution. to see how long it runs for, run ```
time php *script.php*
```. Look for consistency.

---

### Post by new_tolinux on 2010-03-27
It is affected by max execution.
You have to create a line in your script which sets the execution time:
Example:
```
ini_set("max_execution_time", 90);
```
Sets 90 seconds.

Extra info: Everytime this line runs, the counter is reset. And only PHP-used-time is counted.
Example:
```
<?
$query="some query that takes about an hour to process";
$i=0;
do {
mysql_query($query);
$i++;
}
while ($i < 100);
echo "Ready";
?>
```
This will run perfect. The only problem in Windows can be Internet Explorer which has some self-defined-max-execution-time before it displays a "could not connect" error. Both Firefox and the command-line will even wait for the full 100 hours and the script wil keep running.

---

### Post by Creek on 2010-03-28
Thanks for the reply guys.

When I run the CLI I do it with -n flag (without php.ini) and I run it with set_time_limit(0) which sets the max execution time to unlimited, so it's not that.

It does not give any error when it breaks (which rules out memory allocation).

So I think it's a null byte (EOF) being received in the stream, so I've changed the while(true) to a while(!feof($socket)) and an echo after the loop to see if it breaks.

The script has now been running for two straight hours, so it's probably a php error, not a cli issue.

Cheers.

---

