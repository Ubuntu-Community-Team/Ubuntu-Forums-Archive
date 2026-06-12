---
title: "VIRTUAL HOST Script - Feel Free to use or change"
date: 2013-01-20
forum: Server Platforms
---

### Post by chrisguk on 2013-01-20
Hi all,

I knocked up the following bash script because as a PHP dev I was fed up with manually going in and out of files to add a virtual host.

Now I know there are applications like ISPConfig3 and Webmin but personally I hate those things because its so easy to mess your server up if you dont know what you are doing.

Prerequisites:

You will have a DNS server active and you want to setup your web server on that machine.  Your development files are also located there, but you can change this if you want.

I am sure there could be many modifications to the script below and feel free to post any that you may have.

I know when using automated processes the use of "clear" is not good because most like to see the transaction history.  But I like a clean screen:

Save the file as "vhosts.sh"

The change the execute permissions:

sudo chmod +x vhosts-sh

You can run the file by executing:

sudo ./vhosts.sh

```
#!/bin/bash
#Check for root
true="true"true="true"
ROOT_UID=0
overwrite=""
if [ "$UID" -ne "$ROOT_UID" ]; then
    echo "Must be run as root, use sudo."
    exit 0
fi
clear
echo " 
#     # #     #
#     # #     #   ####    ####    #####
#     # #     #  #    #  #          #
#     # #######  #    #   ####      #
 #   #  #     #  #    #       #     #
  # #   #     #  #    #  #    #     #
   #    #     #   ####    ####      #

 #####
#     #  ######   #####  #    #  #####
#        #          #    #    #  #    #
 #####   #####      #    #    #  #    #
      #  #          #    #    #  #####
#     #  #          #    #    #  #
 #####   ######     #     ####   #
                    
" 
echo ""
echo ""
echo ""
echo ""
echo "Hit [ENTER] to continue ................."
read enter; 
clear

#  Lets ask some questions
     
echo "Enter a domain server Alias (e.g. bart.home):";
read domain;
clear

echo "Enter a Virtual Host Name (e.g. [http://dummy] dummy would be"
echo "your host name or [http://dummy.local] - dummy.local would be your host name )"
read vhname
clear

#  Create the file in /etc/apache2/sites-available

touch /etc/apache2/sites-available/${vhname}
#  setup a folder for the Error logs
mkdir /var/www/domains/${vhname}

#  Check to see if you having a working folder in the document root

    echo "Do you have a folder for the website http://${vhname} in \"/var/www\" already? (y/n)"
    read Question

#  Lets check the logic for the answer to the line above

        if [[ "${Question}" == "no" ]] || [[ "${Question}" == "n" ]]; then

            echo "What would you like to call the folder (no spaces or unusual characters) in /var/www:";
            read NewFolder;

            clear

#  Create the new folder

            mkdir /var/www/${NewFolder}

#  Make sure we have the right permissions

            echo "To enable the correct folder permissions please enter the user (example: user):";
            read user;
            clear
            echo "Now enter the group (this could be \"nogroup\" example user:group):";
            read group;
            clear
            chmod -R 0644 /var/www/${NewFolder}
            chown -R ${user}:${group} /var/www/${NewFolder}

#  Insert the VirtualHost block into the file created /etc/apache2/sites-available

	    echo "
            #${vhname}.${domain}
	    <VirtualHost *:80>
		    ServerName ${vhname}
		    ServerAlias ${vhname}.${domain}
		    ServerAdmin admin@${vhname}
		    DocumentRoot /var/www/${NewFolder}/
		    <Directory /var/www/${NewFolder}/>
		            AllowOverride all
		            Order allow,deny
		            allow from all
		   </Directory>
	    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
		    <Directory "/usr/lib/cgi-bin">
		            AllowOverride None
		            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		            Order allow,deny
		            Allow from all
		    </Directory>	
ErrorLog /var/www/domains/${vhname}/apache.error.log
CustomLog /var/www/domains/${vhname}/apache.access.log common
                                                                                                                                     
	    </VirtualHost>" >> /etc/apache2/sites-available/${vhname}
	    
#   If you have a folder already then do this 

        elif [[ "${Question}" == "yes" ]] || [[ "${Question}" == "y" ]]; then


	    echo "Please confirm and type the name of your folder in /var/www ?"
	    read ExistingFolder
		clear

#  Insert the VirtualHost block
            echo "        
	    ### ${vhname}.${domain}
	    <VirtualHost *:80>
		    ServerName ${vhname}
		    ServerAlias ${vhname}.${domain}
		    ServerAdmin admin@${vhname}
		    DocumentRoot /var/www/${ExistingFolder}/
		    <Directory /var/www/${ExistingFolder}/>
		            AllowOverride all
		            Order allow,deny
		            allow from all
		   </Directory>
	    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
		    <Directory "/usr/lib/cgi-bin">
		            AllowOverride None
		            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		            Order allow,deny
		            Allow from all
		    </Directory>
ErrorLog /var/www/domains/${vhname}/apache.error.log
CustomLog /var/www/domains/${vhname}/apache.access.log common                                                                                
	    </VirtualHost>" >> /etc/apache2/sites-available/${vhname}
        fi
                    

function progress(){
    echo -n "Testing configuration Please wait..."
	sleep 5
    while true
    do
         echo -n "."
         sleep 10
    done
    }

function dotest(){
    apache2ctl configtest
    echo ""
	sleep 5
	clear
    }

# Start it in the background
progress &

# Save PID
ME=$!

# Start the test
dotest

# Kill process
kill $ME &>/dev/null
clear
echo -n "...done."
sudo ln -s /etc/apache2/sites-available/${vhname} /etc/apache2/sites-enabled/${vhname}
clear
echo "Would you like me to restart the server? (y/n)"
read qServer
if [[ "${qServer}" == "yes" ]] || [[ "${qServer}" == "y" ]]; then
                     apache2ctl restart   
                echo "Apache Setup complete"
		
        elif [[ "${qServer}" == "no" ]] || [[ "${qServer}" == "n" ]]; then
            echo ""
fi
clear
echo "Lets setup the domain in the BIND9 server, hit [ENTER] to continue....."
read any
clear
echo "Enter the ServerName (ns1 or ns2 etc):";
read server;
clear
echo "Is the name of the zone file the same as the Domain Name? (y/n)"
read q
    if [[ "${q}" == "no" ]] || [[ "${q}" == "n" ]]; then

    echo "Enter the name of the name of the domain, example:format (bart.home):"
    read servdomain
	echo "${vhname}     IN    CNAME    ${server}" >> /etc/bind/zones/${servdomain}".db"
    echo ""
        elif [[ "${q}" == "yes" ]] || [[ "${q}" == "y" ]]; then

            echo "${vhname}     IN    CNAME    ${server}" >> /etc/bind/zones/${domain}".db"
	fi
echo "Would you like to restart the BIND9 service? (y/n)"
read q
clear
if [[ "${q}" == "yes" ]] || [[ "${q}" == "y" ]]; then
                     
        /etc/init.d/bind9    restart
        	echo ""
                echo " 
  ####   ######   #####  #    #  #####
 #       #          #    #    #  #    #
  ####   #####      #    #    #  #    #
      #  #          #    #    #  #####
 #    #  #          #    #    #  #
  ####   ######     #     ####   #


  ####    ####   #    #  #####   #       ######   #####  ######
 #    #  #    #  ##  ##  #    #  #       #          #    #
 #       #    #  # ## #  #    #  #       #####      #    #####
 #       #    #  #    #  #####   #       #          #    #
 #    #  #    #  #    #  #       #       #          #    #
  ####    ####   #    #  #       ######  ######     #    ######
                                    
                    
"       
elif [[ "${q}" == "no" ]] || [[ "${q}" == "n" ]]; then
            echo "Once you have completed your configuration remember to restart the BIND9 service!"

        fi
```

---

### Post by chrisguk on 2013-01-22
I am going to build on the above as it is kinda custom to fit my needs.  I want to add lots of variables and other questions to fit the general setup of other users server setup as I understand that not everyone is using their server as a DNS Server.

Any suggestions will be warmly welcomed.

---

