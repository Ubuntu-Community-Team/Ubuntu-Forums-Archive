---
title: "Trouble with php update script for SugarCRM"
date: 2011-04-06
forum: Server Platforms
---

### Post by jrdonnaruma on 2011-04-06
Hello All,

I have recently inherited a SugarCRM that needs desperately to be updated. I was originally going to do a fresh install, and move contacts over but I cannot get the export function to work on the system for some reason (a totally different issue) So I figured I would go for the upgrade. Here is the problems, when I try to do an upgrade on the Admin panel, the wizard will not load, I get the CRM header and left side bar, and where the information should be to upload, it doesn't render. 

So I decided to try to use the silentUpgrader, and it fails out with a "PHP Fatal Error: Call to a member function read() on a non-object in /var/www/sugar/include/dir_inc.php on line 151". After searching the forums, I thought I had an issue with permissions, but the /var/www folders and subfolders are all rwx by the web server, (did a chown -R <webserver-user:webserver:user> /var/www/sugar and a chmod -R 7777 /var/www/sugar just to make sure). But it is still not running. Even running the script as root doesn't work. (my permissions are set back to 766 now.

Any help would be lovely, I'm trying to get this project finished before I leave for Boston this weekend.

System:
PHP 5.3
Apache 2
Sugar 5.0

Justin R. Donnaruma
Web Applications / Social Media Guru
Maine Energy Systems ( maineenergysystems.com )

---

### Post by DaithiF on 2011-04-07
Hi,
most likely a function in dir_inc.php is being asked to find files within a directory which doesn't exist or is not accessible.  your best bet is to add logging statements to that file to find out which directory that is, and from there figure out what piece of code is trying to do that and why.

Line numbers will vary by version of SugarCRM, e.g. line 151 of dir_inc.php in my version does not have a call to read() ... the closest read() for me is line 159 in the function findAllFiles: 

```
    $d = dir($the_dir);
[B]    while( $f = $d->read() ) {
[/B]        if( $f == "." || $f == ".." ){
            continue;
        }

```
I would suggest you add a logging statement just before the line with the read() command:
```
$GLOBALS['log']->info("Going to read directory: " . $the_dir);
```

Secondly, I would guess that the code most likely calling this function is in modules/Administration/UpgradeWizard_prepare.php, in particular line 191 (in my version, yours may differ), which does:
```
$new_files      = findAllFilesRelative( "$unzip_dir/$zip_from_dir", array() );

```
(findAllFilesRelative exists in dir_inc.php and in turn calls the findAllFiles function where the read() error is most likely occurring.)
Again you could add a logging statement to output the value of $unzip_dir and $zip_from_dir and see whether they exist and are accessible.

good luck

---

### Post by jrdonnaruma on 2011-04-07
Thanks for the reply! I'll give that a try and see what it produces.

---

