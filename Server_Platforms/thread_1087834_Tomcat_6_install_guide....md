---
title: "Tomcat 6 install guide..."
date: 2009-03-05
forum: Server Platforms
---

### Post by Shpongle on 2009-03-05
i found this on the web & it works so i thought id share it with yous here  :)


Installing Tomcat 6 on Ubuntu

If you are running Ubuntu and want to use the Tomcat servlet container, you should not use the version from the repositories as it just doesn't work correctly. Instead you'll need to use the manual installation process that I'm outlining here.

Before you install Tomcat you'll want to make sure that you've installed Java. I would assume if you are trying to install Tomcat you've already installed java, but if you aren't sure you can check with the dpkg command like so:

    dpkg –get-selections | grep sun-java

This should give you this output if you already installed java:

    sun-java6-bin                                   install
    sun-java6-jdk                                   install
    sun-java6-jre                                   install

If that command has no results, you'll want to install the latest version with this command:

    sudo apt-get install sun-java6-jdk

Installation

Now we'll download and extract Tomcat from the apache site. You should check to make sure there's not another version and adjust accordingly.

    wget [http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz](http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz)

    tar xvzf apache-tomcat-6.0.14.tar.gz

The best thing to do is move the tomcat folder to a permanent location. I chose /usr/local/tomcat, but you could move it somewhere else if you wanted to.

    sudo mv apache-tomcat-6.0.14 /usr/local/tomcat

Tomcat requires setting the JAVA_HOME variable. The best way to do this is to set it in your .bashrc file. You could also edit your startup.sh file if you so chose.

The better method is editing your .bashrc file and adding the bolded line there. You'll have to logout of the shell for the change to take effect.

    gedit ~/.bashrc

Add the following line:

    export JAVA_HOME=/usr/lib/jvm/java-6-sun

At this point you can start tomcat by just executing the startup.sh script in the tomcat/bin folder.

Automatic Starting

To make tomcat automatically start when we boot up the computer, you can add a script to make it auto-start and shutdown.

    sudo gedit /etc/init.d/tomcat

Now paste in the following:

    # Tomcat auto-start
    #
    # description: Auto-starts tomcat
    # processname: tomcat
    # pidfile: /var/run/tomcat.pid

    export JAVA_HOME=/usr/lib/jvm/java-6-sun

    case $1 in
    start)
            sh /usr/local/tomcat/bin/startup.sh
            ;;
    stop)  
            sh /usr/local/tomcat/bin/shutdown.sh
            ;;
    restart)
            sh /usr/local/tomcat/bin/shutdown.sh
            sh /usr/local/tomcat/bin/startup.sh
            ;;
    esac   
    exit 0

You'll need to make the script executable by running the chmod command:

    sudo chmod 755 /etc/init.d/tomcat

The last step is actually linking this script to the startup folders with a symbolic link. Execute these two commands and we should be on our way.

    sudo ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
    sudo ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat

Tomcat should now be fully installed and operational. Enjoy!

---

### Post by slick_rick on 2009-03-30
Following these instruction would result tomcat running as root.  Is that what you intended?

What problem exactly did you have with the packaged tomcat?

---

### Post by mstrello on 2009-04-08
Of course I'm not sure, but apparently there are a lot of prerequisites if you want to install tomcat6 from the repository:

  gcj-4.3-base jsvc libcommons-collections-java libcommons-daemon-java
  libcommons-dbcp-java libcommons-pool-java libecj-java libecj-java-gcj
  libgcj-bc libgcj-common libgcj9-0 libgcj9-jar libservlet2.5-java
  libtomcat6-java tomcat6-common

(as reported by apt-get -s install tomcat6).

I want to use only the java environment from Sun. Why I need the others?

Best regards,
--
Mauricio Strello C.

---

### Post by Shpongle on 2009-04-09
i just followed the instructions outlined above and it worked for me, i found it here [http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

mabye the original author could help you out more, as far as i know i didnt have to install any other packages other than the ones outlined . i didnt try to install the packaged one due to the warning in the post, so i dont actually know if the packaged one works or not?

---

### Post by faizan_comsian on 2009-07-19
HEllO:
Please help me out

i did the steps of instalation of java but after that when i checked java existance by ur command as u mentioned it show me this result:


 dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

PLZ GUIEDE ME WHAT THAT MEANS

---

### Post by lbornov2 on 2009-07-28
BTW... if you guys really want to check if Tomcat got installed correctly, do:
[http://127.0.0.1:8080/](http://127.0.0.1:8080/)

Tomcat defaults to port 8080...

Also for refernce, the "JAVA_PATH" is usually "/usr/lib/jvm/<your version of java>" if you installed the binaries (sudo apt-get.. )

---

### Post by saracen75 on 2009-09-24
> **faizan_comsian said:**
> HEllO:
Please help me out

i did the steps of instalation of java but after that when i checked java existance by ur command as u mentioned it show me this result:


 dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

PLZ GUIEDE ME WHAT THAT MEANS


Hello Faizan,

The original command is missing a "-" character. Try this:

dpkg --get-selections | grep sun-java

---

### Post by micio8 on 2009-11-09
Hi,
when i typt the following line I get an error....Can you HELP PLEASE?

fabio@ubuntu01:~$ tar xvzf apache-tomcat-6.0.20.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
fabio@ubuntu01:~$ 

Thanks

---

### Post by Alemacito on 2010-08-11
Hi every body,

I've followed the install instrucction just as the first post but I can't reach the server start, when i run the ./startup.sh i recive the next:

alemancito@alemancito-desktop:/usr/local/tomcat/bin$ sudo ./startup.sh 
[sudo] password for alemancito: 
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /usr/local/tomcat/bin/bootstrap.jar

and when i check the server status open the url:localhost:8080 it does not working at all, also i'have
run a netstat to check the por but:

alemancito@alemancito-desktop:/usr/local/tomcat/bin$ sudo netstat -plut
Conexiones activas de Internet (solo servidores)

Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado       PID/Program name
tcp        0      0 localhost:ipp           *:*                     ESCUCHAR    1120/cupsd      
tcp        0      0 localhost:postgresql    *:*                     ESCUCHAR    986/postgres    
tcp6       0      0 localhost:ipp           [::]:*                  ESCUCHAR    1120/cupsd      
tcp6       0      0 localhost:postgresql    [::]:*                  ESCUCHAR    986/postgres    
udp        0      0 *:mdns                  *:*                                 733/avahi-daemon: r
udp        0      0 *:bootpc                *:*                                 883/dhclient    
udp        0      0 *:60256                 *:*                                 733/avahi-daemon: r

if any could help I'll really appreciate it.

---

### Post by ootuoyetahi on 2010-08-18
How about a guide that doesnt run Tomcat as root and shows how to set up SSL.

---

### Post by Kozay9 on 2011-02-19
I created a script for automatic installation of tomcat running on port 80. But it's for tomcat 7, though it can be easily adapted for tomcat 6.

just change the URL where:
[http://mirrors.fe.up.pt/pub/apache/tomcat/tomcat-7/v7.0.8/bin/apache-tomcat-7.0.8.tar.gz](http://mirrors.fe.up.pt/pub/apache/tomcat/tomcat-7/v7.0.8/bin/apache-tomcat-7.0.8.tar.gz)
is:
[http://mirrors.fe.up.pt/pub/apache/tomcat/tomcat-6/v6.0.32/bin/apache-tomcat-6.0.32.tar.gz](http://mirrors.fe.up.pt/pub/apache/tomcat/tomcat-6/v6.0.32/bin/apache-tomcat-6.0.32.tar.gz)

And at the end of tomcat_install.sh where:
     ```
echo '<role rolename="manager-gui"/>'>> tomcat-users.xml
     echo '<role rolename="admin-gui"/>'>> tomcat-users.xml
     echo '<user username="'$TOMCAT_USERNAME'" password="'$TOMCAT_PASSWORD'" roles="manager-gui,admin-gui"/>'>> tomcat-users.xml
```
Stay:
     ```
echo '<role rolename="manager"/>'>> tomcat-users.xml
     echo '<role rolename="admin"/>'>> tomcat-users.xml
     echo '<user username="'$TOMCAT_USERNAME'" password="'$TOMCAT_PASSWORD'" roles="manager,admin"/>'>> tomcat-users.xml
```

tomecat_init_file.sh
```
JSVC=/usr/bin/jsvc

TMP_DIR=/tmp/tomcat
CLASSPATH=$JAVA_HOME/lib/tools.jar
CLASSPATH=$CLASSPATH:$CATALINA_HOME/bin/commons-deamon.jar
CLASSPATH=$CLASSPATH:$CATALINA_HOME/bin/bootstrap.jar
CLASSPATH=$CLASSPATH:$CATALINA_HOME/bin/tomcat-juli.jar

# if user is not set set the user to "tomcat"
if [ -z "$RUN_AS_USER" ]; then
    RUN_AS_USER="TOMCAT_USER"
fi

RETVAL=0

# Start the deamon
start(){
    echo -n "Starting tomcat: "
    chown -R $RUN_AS_USER:$RUN_AS_USER $CATALINA_HOME
    mkdir -p $TMP_DIR
    chown -R $RUN_AS_USER:$RUN_AS_USER $TMP_DIR
    $JSVC -user $RUN_AS_USER \
        -home $JAVA_HOME \
        -Dcatalina.home=$CATALINA_HOME \
        -Djava.io.tmpdir=$TMP_DIR \
        -Djava.awt.headless=true \
        -outfile $CATALINA_HOME/logs/catalina.out \
        -errfile '&1' \
        -cp $CLASSPATH \
        org.apache.catalina.startup.Bootstrap

    RETVAL=$?
    [ $RETVAL = 0 ] && touch /var/lock/tomcat
    return $RETVAL
}

# Stop the deamon
stop(){
    echo -n "Stoping tomcat: "
    PID=$(cat /var/run/jsvc.pid)
    kill $PID
    RETVAL=$?
    [ $RETVAL = 0 ] && rm -f /var/lock/tomcat /var/run/tomcat.pid
    return $RETVAL
}

restart(){
    $JSVC -user $RUN_AS_USER \
        -home $JAVA_HOME \
        -Dcatalina.home=$CATALINA_HOME \
        -Djava.io.tmpdir=$TMP_DIR \
        -Djava.awt.headless=true \
        -outfile $CATALINA_HOME/logs/catalina.out \
        -errfile '&1' \
        -cp $CLASSPATH \
        -stop org.apache.catalina.startup.Bootstrap
    start
}

case "$1" in
    start)
        start
        if [ $? -eq 0 ]; then
            echo "[done]"
        else
            echo "[fail]"
        fi
        ;;
    stop)
        stop
        if [ $? -eq 0 ]; then
            echo "[done]"
        else
            echo "[fail]"
        fi
        ;;
    restart)
        restart
        ;;
    *)
        echo "Usage $0 {start|stop|restart}"
        exit 1
esac
exit $RETVAL

```

tomcat_install.sh
```
#!/bin/bash

if [ -z $CATALINA_HOME ]; then
    CATALINA_HOME="/opt/tomcat"
fi

if [ -z $JAVA_HOME ]; then
    JAVA_HOME="/usr/lib/jvm/default-java/"
fi

if [ -d $CATALINA_HOME ]; then
    echo "Directory $CATALINA_HOME exist..." 1>&2
    echo "Do you went to remove? [y/n]"
    read ANSN
    if [[ "$ANSN" == "y" ]]; then
        rm -rf $CATALINA_HOME
    else
        echo "Define a new CATALINA_HOME"
        exit 1
    fi
fi

if [ "$(id -u)" != "0" ]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi
wget -c http://mirrors.fe.up.pt/pub/apache/tomcat/tomcat-7/v7.0.8/bin/apache-tomcat-7.0.8.tar.gz

if [ -z $TOMCAT_USER ]; then
    TOMCAT_USER="tomcat"
fi

echo "Installing necessary packeges..."
apt-get -y install jsvc sed

echo "Creating user $TOMCAT_USER..."
useradd -s /bin/false -d /dev/null $TOMCAT_USER

echo "Seting up /etc/init.d/tomcat script..."
echo "#!/bin/bash" > /etc/init.d/tomcat
echo "CATALINA_HOME=$CATALINA_HOME" >> /etc/init.d/tomcat
echo "JAVA_HOME=$JAVA_HOME" >> /etc/init.d/tomcat
cat tomcat_init_file.sh | sed s/TOMCAT_USER/$TOMCAT_USER/g >> /etc/init.d/tomcat

chmod +x /etc/init.d/tomcat
update-rc.d tomcat defaults

echo "Extracting tomcat..."
cp apache-tomcat*.tar.gz /opt
cd /opt
tar -xzf apache-tomcat*.tar.gz
rm apache-tomcat*.tar.gz
mv apache-tomcat* tomcat

echo "Do you went to run on port 80? [y/n]"
read ANSN
if [[ "$ANSN" == "y" ]]; then
    cat /opt/tomcat/conf/server.xml | sed s/8080/80/g > server.xml
    mv server.xml /opt/tomcat/conf/server.xml
fi

echo "Add user to tomcat-users.xml? [y/n]"
read ANSN
if [[ "$ANSN" == "y" ]]; then
    TOMCAT_PASSWORD="true"
    TOMCAT_PASSWORD2="false"

    while [[ "$TOMCAT_PASSWORD" != "$TOMCAT_PASSWORD2" ]]; do
        read -p "Username: " TOMCAT_USERNAME
        read -s -p "Password: " TOMCAT_PASSWORD
        echo
        read -s -p "Repeat the Password: " TOMCAT_PASSWORD2
        echo

        if [[ "$TOMCAT_PASSWORD" != "$TOMCAT_PASSWORD2" ]]; then
            echo "The passwords don't match! Repeat the process" 1>&2
        fi
    done
    head -35 /opt/tomcat/conf/tomcat-users.xml > tomcat-users.xml
    echo '  <role rolename="manager-gui"/>' >> tomcat-users.xml
    echo '  <role rolename="admin-gui"/>' >> tomcat-users.xml
    echo '  <user username="'$TOMCAT_USERNAME'" password="'$TOMCAT_PASSWORD'" roles="manager-gui,admin-gui"/>' >> tomcat-users.xml
    echo '</tomcat-users>' >> tomcat-users.xml
    mv tomcat-users.xml /opt/tomcat/conf/tomcat-users.xml
fi
```

Files tomcat_install.sh and tomcat_init_file.sh must be present in the same directory. Now just run:
```
$ sudo ./ tomcat_install.sh
```

forgive my English, but I think it's understandable.

---

### Post by watsoncj on 2011-03-07
It's much easier to just use the built in packages.

See this article for the correct way to allow tomcat to run on a privileged port without running as root:

[http://blogs.mulesoft.org/a-better-tomcat-for-ubuntu-and-debian/comment-page-1/#comment-6986](http://blogs.mulesoft.org/a-better-tomcat-for-ubuntu-and-debian/comment-page-1/#comment-6986)

---

