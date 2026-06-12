---
title: "OSSEC eb ui setup help"
date: 2008-06-13
forum: Security
---

### Post by TuckLive on 2008-06-13
I'm trying to setup the web ui for OSSEC.  I installed it and everything, but when I go to the url given I get the following error message:

Warning: opendir(/var/ossec) [function.opendir]: failed to open dir: No such file or directory in /var/www/ossec-wui-0.3/lib/os_lib_handle.php on line 94
Unable to access ossec directory.

The directory that all my files are under is ossec-wui-0.3.  Will changing the name of the directory to ossec fix this?

---

### Post by pytheas22 on 2008-06-13
I had this problem too.  It's probably because you need to make sure that the line for ossec in /etc/group reads:
```

ossec:x:1001:www-data
```

which is slightly different than what the WUI installation tutorial says.  That solved it for me.

---

### Post by TuckLive on 2008-06-13
That's exactly what I have :(

---

### Post by pytheas22 on 2008-06-13
In that case, did you check to make sure that /var/www/ossec-wui-0.3/lib/os_lib_handle.php exists and has world-readable permissions?

---

### Post by TuckLive on 2008-06-13
that file exists and for the command ls -l I got -rwxr-xr-x 1

---

### Post by TuckLive on 2008-06-13
lines 90 through EOF.  I highlighted 94 where my error message is alerting.  Not having any agents setup yet wouldn't cause this would it?

               $ossec_handle{'notify_time'} = 1200;

               $dh = NULL;
line 94 --->   if($dh = opendir($dir))
               {
                  closedir($dh);
                  $ossec_handle{'dir'} = $dir;
                  $ossec_handle{'agent_dir'} = $dir."queue/agent-info";
                
                  return($ossec_handle);
                }
                return(NULL);
                }
                EOF

---

### Post by pytheas22 on 2008-06-13
Try adding in a line like echo "dh = $dh; dir = $dir"; at that part of the file and see if you can figure out what values are being assigned to $dh and $dir.  I guess one of them is a file that the server doesn't want to open.

---

### Post by TuckLive on 2008-06-14
dh = ;dir = /var/ossec

---

### Post by pytheas22 on 2008-06-14
Well that explains it; dh is not being assigned any value, hence the inability to open the file.  I guess the only way to figure it out is to look at the whole script and trace down where dh is supposed to be getting a value from, and figure out why it's not.  It shouldn't be too hard, though; just open the script in gedit and search for dh.  If you don't know php and can't figure it out you can post the script here and I'll take a look.  I don't have access to an OSSEC server anymore because I no longer work at the place where we used it, so I can't look at the script myself, and I don't want to have to install the WUI on my personal computer.

---

### Post by TuckLive on 2008-06-14
Here is my file.  I do see this line $dh = NULL; but I'm not sure what to put their if anything.  I'm looking through it now, but maybe you can help me faster.  I appreciate all your help so far.

```
<?php
/* @(#) $Id: os_lib_handle.php,v 1.9 2008/03/03 19:37:25 dcid Exp $ */

/* Copyright (C) 2006-2008 Daniel B. Cid <dcid@ossec.net>
 * All rights reserved.
 *
 * This program is a free software; you can redistribute it
 * and/or modify it under the terms of the GNU General Public
 * License (version 3) as published by the FSF - Free Software
 * Foundation
 */
       
/**
 * This file contains functions dealing with the retrieval of firewall alert
 * related information from an OSSEC installation.
 * 
 * @copyright Copyright (c) 2006-2008, Daniel B. Cid, All rights reserved.
 * @package ossec_web_ui
 * @author  Daniel B. Cid <dcid@ossec.net>
 * @license http://www.gnu.org/licenses/gpl-3.0.txt GNU Public License
 * 
 */

/**
 * Verify that the given configuration items are set. Returns
 * NULL on error.
 *
 * @param unknown_type $ossec_dir
 * @param unknown_type $ossec_max_alerts_per_page
 * @param unknown_type $ossec_search_level
 * @param unknown_type $ossec_search_time
 * @param unknown_type $ossec_refresh_time
 * @return unknown
 */
function os_check_config($ossec_dir, $ossec_max_alerts_per_page,
                         $ossec_search_level, $ossec_search_time,
                         $ossec_refresh_time)
{
    $config_err = "<b class='red'>Configuration error. Missing '%s'.</b><br />";
    
    /* checking each config variable */
    if(!isset($ossec_dir))
    {
        echo sprintf($config_err, '$ossec_dir');
        return(0);
    }

    if(!isset($ossec_max_alerts_per_page))
    {
        echo sprintf($config_err, '$ossec_max_alerts_per_page');
        return(0);
    }

    if(!isset($ossec_search_level))
    {
        echo sprintf($config_err, '$ossec_search_level');
        return(0);
    }

    if(!isset($ossec_search_time))
    {
        echo sprintf($config_err, '$ossec_search_time');
        return(0);
    }

    if(!isset($ossec_refresh_time))
    {
        echo sprintf($config_err, '$ossec_refresh_time');
        return(0);
    }
    
    return(1);
}


/**
 * Set the handle directory and create the ossec handler.
 *
 * @param unknown_type $dir
 * @return unknown
 */
function os_handle_start($dir)
{
    $ossec_handle{'dir'} = NULL;
    $ossec_handle{'agent_dir'} = NULL;
    $ossec_handle{'name'} = NULL;
    $ossec_handle{'error'} = NULL;


    /* 20 minutes */
    $ossec_handle{'notify_time'} = 1200;

    $dh = NULL;
   echo "dh = $dh;dir = $dir";
    if($dh = opendir($dir))
    {
        closedir($dh);
        $ossec_handle{'dir'} = $dir;
        $ossec_handle{'agent_dir'} = $dir."/queue/agent-info";
        
        return($ossec_handle);
    }
    return(NULL);
}


/* EOF */
?>
```

---

### Post by pytheas22 on 2008-06-14
What happens if you comment out this whole if statement:
```

if($dh = opendir($dir))
    {
        closedir($dh);
        $ossec_handle{'dir'} = $dir;
        $ossec_handle{'agent_dir'} = $dir."/queue/agent-info";
        
        return($ossec_handle);
    }
```

does it work then?

Or if that doesn't work, comment or erase the whole function.  I can't find anywhere where it's being called anyway, and I'm not a php expert, but I'm pretty sure that the whole if statement is malformed...the = should be ==.

---

### Post by TuckLive on 2008-06-14
commenting out that section I get "cannot access ossec directory"

When I comment out the entire function I get "You are not allowed direct access"

---

### Post by pytheas22 on 2008-06-14
Sorry, it turns out that the function does get called at the top of some of the files in /site, like /site/main.php.

What if you comment just the $dh = NULL; line?

---

### Post by TuckLive on 2008-06-14
Uncommenting out the function and just the line you recommended comes back with the original error message.

---

### Post by pytheas22 on 2008-06-14
> Uncommenting out the function and just the line you recommended comes back with the original error message. 

Alright, I'm not really sure what to do next then.  We could probably figure this out if we try hard enough but I think it would be more efficient to just send a message to the OSSEC list asking about it.  The main OSSEC developer, Daniel Cid, is very good about responding, and I'm sure he'll have a much better idea what's wrong than either of us.  You can get instructions for the list at [http://www.ossec.net/main/support/#ossec-list](http://www.ossec.net/main/support/#ossec-list) .

---

### Post by TuckLive on 2008-06-22
Found the problem.  I had to edit my ossec_conf.php file to point to /var/www/ossec.  It was looking for /var/ossec.

---

