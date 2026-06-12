---
title: "Need help with very simple php script"
date: 2007-03-05
forum: The Cafe
---

### Post by mikestefff on 2007-03-05
This script im trying to create reads through every line of a file which includes blacklisted ip's. it then compares the time they got blacklisted with the current time. if its been 45 minutes i want the line removed from the file. i dont know php so i do know how to remove a line from the file being read. i am sure its very easy and if someone could help that would be great. (the script also moves the line thats going to be deleted into a seperate file to be archived)

---

```
<?php

    $filename = "blacklist.dat";

    $filename2 = "blacklistark.dat";

    $fp = fopen($filename, "r");

    $fp2 = fopen($filename2,'a+');

    $tmestamp = time();

    while ($line = fgets($fp,255))  {

      $u = explode(" ",$line);

      $time = $u[6];

      print $tmestamp - $time;

        //45 minutes

      if(($tmestamp - $time) > 2700) {
       //NEED TO DELETE THE LINE HERE

        //add deleted line to archive

        fwrite($fp2, $line);



      }

    }

    fclose($fp2);

    fclose($fp);

?>


```

---

### Post by natedawg on 2007-03-05
Well I know a good amount of PHP but I don't have the time at the moment to type up a working example. If you need help with PHP the Ubuntu forums is not the first place I would try. I would suggest that you go to the community at [http://www.phpbuilder.com](http://www.phpbuilder.com) for help, I always find good solutions there.

---

