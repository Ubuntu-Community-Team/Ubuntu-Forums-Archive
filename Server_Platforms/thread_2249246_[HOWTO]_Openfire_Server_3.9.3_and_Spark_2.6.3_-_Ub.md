---
title: "[HOWTO] Openfire Server 3.9.3 and Spark 2.6.3 - Ubuntu 14.04 Server and 14.04 Desktop"
date: 2014-10-20
forum: Server Platforms
---

### Post by matt_fussell2 on 2014-10-20
Prior to posting this I hadn't found a complete solution for installing and running Openfire server and Spark clients in Ubuntu 14.04. This thread will provide those solutions along with the appropriate installation scripts for both; hopefully you find it useful.

The server script was verified on a KVM-hosted instance of Ubuntu 14.04 server. The Spark client would launch on a KVM-hosted instance Ubuntu 14.04 Desktop, but when connecting to the server would crash. When Ubuntu 14.04 Desktop was installed on bare metal, the spark client functioned as expected.

This script assumes that a fresh install of Ubuntu 14.04 Server has been installed:

```

#!/bin/bash
# written for Ubuntu 14.04 Server
# This script distilled from instructions found at:
# http://ubuntuserverguide.com/2013/01/how-to-setup-chat-server-using-openfire-in-ubuntu-server-12-04.html

# A few recommendations: a static IP address is best for servers.
# SSH access is generally a positive thing as well. Both are outside
# the scope of this script - if you need help, hit me up on the forums.
# This script will assume you have done both.

# Root access will speed this entire process up; run this as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

# Update the server, skipping the prompts
apt-get update
aptitude safe-upgrade -y 
apt-get autoremove -y
apt-get autoclean -y

# Install Oracle Java (I know, not FOSS, but necessary), again
# without prompts because we mean to do what we're doing.
apt-get install python-software-properties -y
add-apt-repository ppa:webupd8team/java -y 
apt-get update
apt-get install -y oracle-java7-installer

# This script will use the default HSQLDB option for the Openfire 
# install - there are options for using other databases; check
# the URL at the top of the script for suggestions

# Retrieve the installer for Openfire; this will need updated 
# from release-to-release; this works for now.
wget http://www.igniterealtime.org/builds/openfire/openfire_3.9.3_all.deb
dpkg -i openfire_3.9.3_all.deb

# At this point you should be ready to go
# http://mydomain:9090/setup/index.jsp
# and start setting up specifics about your server. Remember to select the
# default HSQLDB as this script did not install another database option.

# Once you have configured your server, it will tell you which ports you need
# to have open in your firewall (firewall config instructions not included in
# this script).

```

This script assumes a fresh install of Ubuntu 14.04 Desktop has been installed:

```

#!/bin/bash
# written for Ubuntu 14.04 Desktop
# This script distilled from instructions found at:
# http://www.2daygeek.com/how-to-install-spark-im-client-in-ubuntu-14-04/
# https://community.igniterealtime.org/thread/51193

# This script installs the Spark client for the Openfire XMPP server.
# It assumes that you have just installed the OS - check the section
# after root verification to make sure that you have the necessary software
# and adjust accordingly if you have already installed the required packages

# Root access will speed this entire process up; run this as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

# Update the local machine and install necessary
# software, skipping the prompts
apt-get update
apt-get install -y aptitude jitsi lib32z1 libxi6 libxi6:i386 libxtst6 libxtst6:i386 libxt6:i386 #openjdk-7-jre-headless 
aptitude safe-upgrade -y 
apt-get autoremove -y
apt-get autoclean -y

# Download the Spark client
wget http://www.igniterealtime.org/builds/spark/spark_2_6_3.tar.gz

# Unzip the file
tar -xzvf spark_2_6_3.tar.gz

# Make a new home for the Spark client, then move it
mkdir /opt/spark
cp -r Spark/lib/windows64 Spark/lib/windows
cp -r Spark/* /opt/spark
chmod -R 777 /opt/spark

# Create the spark launcher
launcher="/usr/share/applications/spark.desktop"
touch $launcher

echo "[Desktop Entry]" >> $launcher
echo "Name=Spark" >> $launcher
echo "Version=2.6.3" >> $launcher
echo "GenericName=Spark" >> $launcher
echo "X-GNOME-FullName=Spark" >> $launcher
echo "Comment=ignite realtime Spark IM client" >> $launcher
echo "Type=Application" >> $launcher
echo "Categories=Application;Utility;" >> $launcher
echo "Path=/opt/spark" >> $launcher
echo "Exec=/bin/bash Spark" >> $launcher
echo "Terminal=false" >> $launcher
echo "StartupNotify=true" >> $launcher
echo "Icon=/opt/spark/spark.gif" >> $launcher
echo "TargetEnvironment=Unity" >> $launcher

wget http://www.igniterealtime.org/images/ignite_dl_spark.gif
mv ignite_dl_spark.gif spark.gif
mv spark.gif /opt/spark/spark.gif
shutdown now -r

```

You may want to find another image for your Spark launcher, but this one will suffice for the script. [Google image search]("https://www.google.com/search?q=spark+client+image&client=ubuntu&hs=VwK&channel=fs&source=lnms&tbm=isch&sa=X&ei=bGlFVJ3wBKr38AGC3IDIAQ&ved=0CAkQ_AUoAg&biw=1920&bih=953") will return options, but not all of those are specifically tied to the client by Ignite Realtime. There are probably better ways to implement the client, but since there is no .deb installer or repository, this works as a starting point. Feel free to modify the scripts to meet your needs.

---

### Post by matt_fussell2 on 2014-10-20
ADDENDUM - It appears that new client connections (effectively friend requests) have to be conducted in the Spark client, but afterwards it was found to be beneficial to use the Jitsi client as it offered more features (video, shared desktops) than does the Spark client.

---

