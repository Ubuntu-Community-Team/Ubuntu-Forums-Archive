---
title: "Phpmyadmin additional features"
date: 2011-05-16
forum: Server Platforms
---

### Post by Joe325 on 2011-05-16
Hi all,

I recently installed Ubuntu Server 10 04 on a Dell Server and everything seems to be running well - except on logging into phpmyadmin, I get the message " The additional features for working with linked tables have been deactivated. To find out why click here."
Clicking 'Here' shows me:

$cfg['Servers'][$i]['pmadb'] ... 

not OK [ Documentation ]

$cfg['Servers'][$i]['relation'] ... 

not OK [ Documentation ]

General relation features: Disabled

$cfg['Servers'][$i]['table_info'] ... 

not OK [ Documentation ]

Display Features: Disabled

$cfg['Servers'][$i]['table_coords'] ... 

not OK [ Documentation ]

$cfg['Servers'][$i]['pdf_pages'] ... 

not OK [ Documentation ]

Creation of PDFs: Disabled

$cfg['Servers'][$i]['column_info'] ... 

not OK [ Documentation ]
Displaying Column Comments: Disabled
Browser transformation: Disabled
$cfg['Servers'][$i]['bookmarktable'] ... 
not OK [ Documentation ]

Bookmarked SQL query: Disabled

$cfg['Servers'][$i]['history'] ... 

not OK [ Documentation ]

SQL history: Disabled

$cfg['Servers'][$i]['designer_coords'] ... 

not OK [ Documentation ]
Designer: Disabled
$cfg['Servers'][$i]['tracking'] ... 

not OK [ Documentation ]
Tracking: Disabled

Everythings disabled. I have set 1 up before and just had to add the [tracking] entry to get rid of the message but this time, it didnt do it.

My config file looks like this :

 /* Authentication type */
    $cfg['Servers'][$i]['auth_type'] = 'cookie';
    /* Server parameters */
    if (empty($dbserver)) $dbserver = 'localhost';
    $cfg['Servers'][$i]['host'] = $dbserver;

    if (!empty($dbport)) {
        $cfg['Servers'][$i]['connect_type'] = 'tcp';
        $cfg['Servers'][$i]['port'] = $dbport;
    }
    //$cfg['Servers'][$i]['compress'] = false;
    /* Select mysqli if your server has it */
    $cfg['Servers'][$i]['extension'] = 'mysqli';
    /* Optional: User for advanced features */
    $cfg['Servers'][$i]['controluser'] = $dbuser;
    $cfg['Servers'][$i]['controlpass'] = $dbpass;
    /* Optional: Advanced phpMyAdmin features */
    $cfg['Servers'][$i]['pmadb'] = $dbname;
    $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
    $cfg['Servers'][$i]['history'] = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';
    $cfg['Servers'][$i]['tracking'] = 'pma_tracking';

    /* Uncomment the following to enable logging in to passwordless accounts,
     * after taking note of the associated security risks. */
    // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;

    /* Advance to next server for rest of config */
    $i++;


 
I have checked this file against the 1 I got working previously and its identical. Any one know what might be the issue here?

Thanks

---

### Post by Joe325 on 2011-05-17
Actually, now I noticed Im missing the actual phpmyadmin database within

---

### Post by Joe325 on 2011-05-17
Ive solved this by running:
sudo dpkg-reconfigure phpmyadmin
Choosing yes to install database
Logged in and got only tracking error.
Added the line: $cfg['Servers'][$i]['tracking'] = 'pma_tracking';
to config.inc.php
Logged in - got a new error  "Connection for controluser as defined in your configuration failed".
Commented out the:
$cfg['Servers'][$i]['controluser'] = $dbuser;
$cfg['Servers'][$i]['controlpass'] = $dbpass;

logged back in and worked.:)

---

