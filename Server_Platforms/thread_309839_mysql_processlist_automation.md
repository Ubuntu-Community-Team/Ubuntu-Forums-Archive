---
title: "mysql processlist automation?"
date: 2006-11-30
forum: Server Platforms
---

### Post by tocleora on 2006-11-30
From time to time I get into a situation where I need to monitor the mysql processlist.  It's kind of a pain though having to type "show processlist;", hitting the up arrow and the enter key each time to monitor.  Is there a way to automate this process somehow?  I found mytop but I couldn't get it to work correctly.  I should mention this is for a Fedora Core 4 server :-#, but I didn't get much of a response from them so I thought I'd try here. :)  My new server is Ubuntu so I'm sure I'll use it for that as well, if that makes this more legal! Hah! :p

---

### Post by apjone on 2006-11-30
You could probably display it on a web page that auto refreshes

---

### Post by tocleora on 2006-11-30
Funny, I thought about that a few minutes after posting this. :)  I would like something a little more real time but if there's not anything I'll do that.  Thanks for the suggestion!

---

### Post by tocleora on 2006-12-05
Ok, so here's my quick and dirty solution to the problem in case anyone wants this.  Yeah I used tables, etc. blah blah blah I said quick and dirty. ;)

This is PHP so just write to a php file, put it on your web server and call it in your browser.

Replace "username", "password", "databasename" with appropriate information.

Change the "15" in the META line to how many seconds you want before it refreshes, and "processlist.php" to whatever you call your php file.

```
<html>
<head>
<META HTTP-EQUIV="Refresh" CONTENT="15;URL=processlist.php">
</head>
<body>
<?

$link = mysql_connect ('localhost', 'username', 'password');
mysql_select_db ('databasename');

$bgcolor = '';
$result = mysql_query("show processlist");
if ($row = mysql_fetch_array($result)) {
	echo '<center><table style="font-family: arial,helvetica; font-size: 10pt;" cellpadding="5">';
	echo '<tr style="font-weight: bold;"><td>Host</td><td>Time</td><td>State</td><td>Info</td></tr>';
	do {
		if ($bgcolor == '#F2F2F2') { $bgcolor = 'white'; } else { $bgcolor = '#F2F2F2'; }
		echo '<tr bgcolor="'.$bgcolor.'"><td NOWRAP>'.$row["Host"].'</td><td NOWRAP>'.$row["Time"].'</td><td NOWRAP>'.$row["State"].'</td><td>'.$row["Info"].'</td></tr>';
	} while ($row = mysql_fetch_array($result));
	echo '</table></center>';
}


mysql_close($link);


?>
</body>
</html>
```

---

### Post by mhearse on 2008-02-04
Run this program as a shell script (put the contents in a file and set execute bit).  This is obviously designed to be run from a terminal session.  

```

#!/bin/bash

DELAY=2

while getopts whp: option_read
do
    case $option_read in
        h)  HELP=1
        ;;  
        p)  DELAY=$OPTARG
            echo $DELAY | egrep -v [a-z] | egrep -v [A-Z] ||
                HELP=1
        ;;  
        w)  W3M=1
        ;;  
    esac
done

if [ "$HELP" = 1 ]; then
    cat <<EOH

This program continuously monitors mysql queries.

    -p Pause for x seconds (2 is default).  Must be numeric.

    -w Uses w3m to print a beautified version.  Basically 
       displays the query 

    -h Print help menu

EOH
    exit
fi

cmd="mysqladmin processlist"
[ $W3M ] && cmd="mysql -A -H -e 'show processlist' | w3m -dump -T text/html"

/usr/bin/watch -n $DELAY "$cmd"

```

---

