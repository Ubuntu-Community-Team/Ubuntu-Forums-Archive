---
title: "Rewrite all links within given web page"
date: 2011-02-08
forum: Server Platforms
---

### Post by deekthesqueak on 2011-02-08
I am trying to setup a virtual machine server as a web development environment. Install and setup is going correct but I need help solving an issue. To avoid any accidents I have the apache alias set to www.example.dev instead of www.example.com.  The URL will redirect no problem but I need to find a way to have every instance of a link (example.com) show up as (example.dev) so that whole site will function on the server without linking to the live external site.

I'm using git as a version control system that will push certain commits to my live site and thus want to avoid changing any configuration files to get this desired effect on my virtual machine.

Does anyone have any suggestions of how to do this server side, maybe via PHP, apache2, or any other solution?

---

### Post by volkswagner on 2011-02-08
I would think [Mod_rewrite]("http://httpd.apache.org/docs/2.0/misc/rewriteguide.html") would work.  You could just exclude your .htaccess file when pushing to your live server.  

I'm not sure how much scripting is on your site, but they may be unaffected by the mod_rewrite.  You can also look into 301 redirect rule with .htaccess.

---

### Post by deekthesqueak on 2011-02-08
From what I've read of mod_rewrite it seems to only work on the URL in the browser.  What I want to do is change the links within the HTML document itself.  If this can be done with mod_rewrite I haven't seen an example of it.  

Just to clarify I'm not accessing the webpage from the server itself just my normal browser to check any changes I've made on my website.

---

### Post by SeijiSensei on 2011-02-09
i found myself having to make global changes like this to a site on a number of occasions and eventually wrote a bash script to replace all instances of a string with another one in a set of files:

/usr/local/bin/replaceall
```

#!/bin/bash

if [ "$1" = "" ]
then
    echo "Syntax: replaceall 'string1' 'string2' 'filespec'"
    exit
fi

WD=`pwd`
NOW=`date +%s`
TMP=~/.replaceall
FILES=`ls $3`
mkdir -p $TMP 

for i in $FILES;
do
   TEST=`grep "$1" $i`
   #echo "Checking $i; TEST=$TEST"
   if [ "$TEST" != "" ] 
   then
      echo -n "Replacing '$1' with '$2' in $i"
      # save backup copies
      cp $i $TMP/$NOW/$i.bak
      (sed "s_$1_$2_g" $i > $i.new) && (rm -f $i; mv $i.new $i)
   fi
done

cd $WD

exit 0

```

Make sure to enclose all three arguments in single quotes as the "syntax" line above explains.

Notice that the script uses the underscore character as a delimiter for sed.  If the string you wish to edit includes an underscore, you'll need a different delimiter in the sed command.

Copies of the untransformed files are written to ~/.replaceall, though you'd obviously want to create a complete backup of the site first.  In fact, I'd create the backup in a new directory, run replaceall against its files, and if everything is okay, swap the original and edited directories.

In your case the command
```
cd /path/to/the/website; replaceall 'example\.dev' 'example.com' '*'
```
will convert all instances of "example.dev" to "example.com".  Notice the backslash in the 'example\.dev'.  That's because sed treats the source string as a regular expression, so you need to "escape" the dot to tell sed it's a literal period and not a placeholder.

---

### Post by deekthesqueak on 2011-02-09
Well I figured out how to do what I wanted and I feel rather dense for not finding it sooner.

Apache has a module in 2.2.7 and later called [substitute]("http://httpd.apache.org/docs/2.2/mod/mod_substitute.html"). This does it the trick. 

```
sudo nano /etc/apache2/sites-available/example.dev
```

Under the virtual host or host you want to apply this to add the two following lines.

```
AddOutputFilterByType SUBSTITUTE text/html
Substitute s/example.com/example.dev/
```

Save then enable the module and restart apache
```
sudo a2enmod substitute
sudo /etc/init.d/apache2 restart
```

and BAM! It works.  Now from my reading this may not cover all the files you want since it only targets text/html but you can add additional rules for different MIME types to preform substitutions on.

---

