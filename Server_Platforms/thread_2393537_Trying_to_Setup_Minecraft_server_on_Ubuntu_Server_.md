---
title: "Trying to Setup Minecraft server on Ubuntu Server 18.04"
date: 2018-06-04
forum: Server Platforms
---

### Post by 18tyweslow on 2018-06-04
Hi guys.

Pardon my extreme lack of knowledge when it comes to Ubuntu. I've always worked with Windows and can set up servers very easily, but I'm having a really hard time getting my server to work on my newly bought VPS.

I bought a VPS today via SoYouStart and installed Ubuntu Server 18.04 on it with the intention to run a Minecraft server on it. I figured if I could get that to work, I could also port over my servers for CS:GO, Gmod and Teamspeak. I cannot for the life of me get the server to work. I'm starting with Minecraft right now, I've tried following guides; I cannot get anything to work. Nothing downloads right using wget, the services never work.. I just feel very defeated right now.

If any of you have any experience setting up a modded minecraft server on Ubuntu using command line, please let me know. Or post a link to a forum post/guide. You guys are my only hope right now.

---

### Post by mastablasta on 2018-06-05
what is not working? only wget? you can download it elsewhere and then move it to server via sFTP. 

i don't think it should be that much different than setting it up on windows. install it and run it.

---

### Post by Tadaen_Sylvermane on 2018-06-05
When i get home i can post the script i use to run my four on my lan. Script does it all in ramdisk. You can use it to setup your own script. The guides online imo are way overcomplicated.

No need for systemd services or init scripts. All useless. My script runs purely non privileged user.

---

### Post by slickymaster on 2018-06-05
Thread moved to **Server Platforms** for a better fit

---

### Post by Tadaen_Sylvermane on 2018-06-05
The script I use, along with my crontab on my minecraft user. This user is totally non privileged. Some of the stuff in script is sourced from another file. None of it is relevant to the working of the minecraft server stuff, just additional functions for email alerts and such.

Crontab

```
MAILTO=""
USER=mcserver
MCSERVERS="creative noeanahi osmosis"
# m h  dom mon dow   command
00 */6 * * *    /usr/local/bin/update
@reboot         /usr/local/bin/start $MCSERVERS
*/10 * * * *    /usr/local/bin/backup $MCSERVERS
*/5 * * * *     /usr/local/bin/runtest $MCSERVERS
00 00 * * *     /usr/local/bin/restart $MCSERVERS
```

Script

```
#!/bin/bash# tadaen sylvermane | jason gibson
# minecraft controller


## source ##


. /usr/local/bin/mainsource


## setup ##


create_links stop restart backup start runtest update
server_desktop_select


## variables ##


MCSERVERSITE=https://minecraft.net/en-us/download/server
BACKUPLOC=/data/backups/minecraft
MINECRAFTEXE=/snapraid/data/ssd/minecraftexe
CURRENTSERVERJAR=$(basename $(find /snapraid/data/ssd/minecraftexe/ -type f))


## functions ##


mc_backups() {
	screen -p 0 -S "$1" -X eval 'stuff "save off"\015'
	screen -p 0 -S "$1" -X eval 'stuff "save-all"\015'
	sync
	sleep 10
	if [[ -e "$RAMDISKLOCK" ]] ; then
		rsync -auv --progress --delete /ramdisk/"$1"/* /home/"$USER"/gameworlds/"$1"/
	fi
	case $(date +%I%M) in
		0600|1200)
			if [[ -e "$RAMDISKLOCK" ]] ; then
				tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz /ramdisk/"$1"/*
			else
				tar -czf "$BACKUPLOC"/"$1"."$NOW".tar.gz /home/"$USER"/gameworlds/"$1"/*
			fi
			;;
	esac
	find "$BACKUPLOC"/ -type f -mtime +2 -exec rm -rf {} \;
	screen -p 0 -S "$1" -X eval 'stuff "save-on"\015'
}


mc_server_shutdown_timer() {
	for seconds in 30 20 10 ; do
		screen -p 0 -S "$1" -X eval "stuff \"say server ${2} in ${seconds} seconds.\"\015"
		sleep 10
	done
	screen -p 0 -S "$1" -X eval 'stuff "stop"\015'
}


## begin script ##


if [[ -e /.server.lock ]] ; then
	if [[ "$USER" == "$MCSERVERUSR" ]] ; then
		if [[ "$1" ]] ; then
			for server in "$@" ; do
				TESTLOCK=/home/"$USER"/gameworlds/"$server"/test.lock
				RAMDISKLOCK=/home/"$USER"/gameworlds/"$server"/ramdisk
				INVOCATION="screen -dmS ${server} java -jar ${MINECRAFTEXE}/${CURRENTSERVERJAR} nogui"
				if screen -ls | grep -q "$server" ; then
					case "$SCRIPTCALL" in
						stop|restart)
							for log in hs_err*log *.log.gz ; do
								if [[ -e "$RAMDISKLOCK" ]] ; then
									find /ramdisk/"$server"/ -name "$log" -mtime +10 -exec rm {} \;
								else
									find /home/"$USER"/gameworlds/"$server"/ -mtime +10 -exec rm {} \;
								fi
							done
							mc_backups "$server" &
							mc_server_shutdown_timer "$server" "$SCRIPTCALL" 30 20 10 &
							if [[ "$SCRIPTCALL" == restart ]] ; then
								sleep 35 && start "$server" &
							fi
							;;
						backup)
							mc_backups "$server" &
							;;
						*)
							echo "${server} is running!"
							;;
					esac
				else
					case "$SCRIPTCALL" in
						start)
							if [[ -e "$RAMDISKLOCK" ]] ; then
								if mountpoint -q /ramdisk ; then
									mkdir -p /ramdisk/"$server"/
									rsync -auv --progress /home/"$USER"/gameworlds/"$server"/* /ramdisk/"$server"/
									cd /ramdisk/"$server"/ && $INVOCATION
								else
									echo "ramdisk for ${server} not mounted!"
								fi
							else
								cd /home/"$USER"/gameworlds/"$server"/ && $INVOCATION
							fi
							sleep 10
							start "$server"
							;;
						runtest)
							if [[ ! -e "$TESTLOCK" ]] ; then
								for try in 1 2 3 ; do
									start "$server"
									sleep 20
									if screen -ls | grep "$server" ; then
										break
									else
										if [[ "$try" == 3 ]] ; then
											emergency_email minecraft "$server"
											touch "$TESTLOCK"
										fi
									fi
								done
							fi
							;;					
						*)
							echo "${server} is not running!"
							;;
					esac
				fi
			done
		else
			NEWMCSERVERVERSION=$(curl "$MCSERVERSITE" | grep launcher.mojang | cut -d\/ -f 6)
			NEWMCDOWNLOAD=$(curl "$MCSERVERSITE" | grep launcher.mojang | awk -F\" '{print $2}')
			if [[ ! -e "$MINECRAFTEXE"/minecraft_server."$NEWMCSERVERVERSION".jar ]] ; then
				wget -O "$MINECRAFTEXE"/minecraft_server."$NEWMCSERVERVERSION".jar "$NEWMCDOWNLOAD"
				for file in "$MINECRAFTEXE"/* ; do
					if [[ "$file" != "$MINECRAFTEXE"/minecraft_server."$NEWMCSERVERVERSION".jar ]] ; then
						rm "$file"
					fi
				done
				for server in $(screen -ls | grep Detached | cut -d . -f 2 | awk '{print $1}') ; do
					restart "$server"
				done
			fi
		fi
	fi
fi
exit 0


## end script ##



```

---

### Post by LHammonds on 2018-06-06
I have been running a Minecraft server on Ubuntu since 10.04.

I do not have any comprehensive tutorials since I did the initial install a LOOOOONNNNNGGGGG time ago and would not apply to the current situation.

The main thing is to get things running/working manually, then automate what you have running such as startup, shutdown, update, reboot and backup scripts.


[LIST=1]
[*]You need to determine exactly what kind of Minecraft server you are going to run.  Is it the server.jar file direct from Minecraft.net or is it Spigot?  Running and updating them are wildly different procedures. 
[*]Install Oracle Java 
[*]Create a low-rights user for each Minecraft instance and run it under that user account 
[*]Use the "screen" utility to run your server instances.  You will need to "push" commands to the console which can be scripted such as the "stop" command you can see in demonstrated in Tadaen_Sylvermane's script (thanks for sharing by the way) 
[/LIST]


FYI - I use screen exclusively for all my server instances but I never interact with it directly...always via scripts.  I cannot even remember the keyboard commands to control screen manually hehehe.

I run a vanilla snapshot server and Spigot.  I use a simple script to download the latest snapshot and another script to assemble the latest Spigot build but do not have those documented anywhere yet.

I would love to write up a step-by-step tutorial but have way too many projects on my plate as it is converting my 16.04 servers to 18.04 and updating my existing tutorials.

**EDIT:** Here is the script I use to download the latest server snapshot into /tmp.  Be aware that Mojang changes the manifest from time to time and you have to make adjustments to get the script to work again.  Just verified it works as of today which is version 1.13-pre1

mc-get-snapshot.sh
```

#!/bin/bash
cd /tmp

__MC_JSON_URL='https://launchermeta.mojang.com/mc/game/version_manifest.json'
__DEFAULT_CLIENT_JAR_LOC="$(dirname $0)/src/minecraft_client.jar"
__BASE_DIR=$(dirname $0)

function getJSONData {
        echo $1 | egrep -o "\"$2\": ?[^\}]*(\}|\")" | sed "s/\"$2\"://"
}

function getJSONVal {
        echo $1 | egrep -o "\"$2\": ?\"[^\"]*" | sed "s/\"$2\"://" | tr -d '{}" '
}
MCJSON=$(curl -s $__MC_JSON_URL)
LATEST_VER=$(getJSONVal "$(getJSONData "$MCJSON" latest)" snapshot)

LATEST_URL_DATA=$(echo $MCJSON | egrep -o "\"id\":\"${LATEST_VER}\"[^}]*")
LATEST_VER_URL=$(getJSONVal "$LATEST_URL_DATA" url)

MCURLJSON=$(curl -s $LATEST_VER_URL)
SERVER_JAR_NAME=minecraft_server_${LATEST_VER}.jar

SERVER_URL=$(getJSONVal "$(getJSONData "$MCURLJSON" server)" url)
SERVER_FILE_SHA1=$(getJSONVal "$(getJSONData "$MCURLJSON" server)" sha1)

LOCAL_FILE=$([[ -n $1 ]] && printf $1 || printf /tmp/$SERVER_JAR_NAME)

if [[ -a "${LOCAL_FILE}" ]]; then
  printf "${LOCAL_FILE} exists -- moving to ${LOCAL_FILE}.old\n"
  mv ${LOCAL_FILE} ${LOCAL_FILE}.old
fi

printf "\nDownloading ${SERVER_JAR_NAME}..."
wget -q -O ${LOCAL_FILE} ${SERVER_URL}
printf "\nFile downloaded at: ${LOCAL_FILE}"

printf "\nChecking sha1sum of ${LOCAL_FILE}..."
DOWNLOAD_FILE_SHA1SUM=$(sha1sum ${LOCAL_FILE} | awk '{print $1}')

if [ $(sha1sum "${LOCAL_FILE}" | awk '{print $1}') != "${SERVER_FILE_SHA1}" ]; then
  printf "\nSHA1 of downloaded file does not match!"
  rm ${LOCAL_FILE}
else
  printf "\nSHA1 matches!\n"
fi

```

This script grabs the current release version which is 1.12.2 as of today.

mc-get-server.jar
```

#!/bin/bash
cd /tmp

__MC_JSON_URL='https://launchermeta.mojang.com/mc/game/version_manifest.json'
__DEFAULT_CLIENT_JAR_LOC="$(dirname $0)/src/minecraft_client.jar"
__BASE_DIR=$(dirname $0)

function getJSONData {
        echo $1 | egrep -o "\"$2\": ?[^\}]*(\}|\")" | sed "s/\"$2\"://"
}

function getJSONVal {
        echo $1 | egrep -o "\"$2\": ?\"[^\"]*" | sed "s/\"$2\"://" | tr -d '{}" '
}

MCJSON=$(curl -s $__MC_JSON_URL)
LATEST_VER=$(getJSONVal "$(getJSONData "$MCJSON" latest)" release)

LATEST_URL_DATA=$(echo $MCJSON | egrep -o "\"id\":\"${LATEST_VER}\"[^}]*")
LATEST_VER_URL=$(getJSONVal "$LATEST_URL_DATA" url)

MCURLJSON=$(curl -s $LATEST_VER_URL)
SERVER_JAR_NAME=minecraft_server_${LATEST_VER}.jar

SERVER_URL=$(getJSONVal "$(getJSONData "$MCURLJSON" server)" url)
SERVER_FILE_SHA1=$(getJSONVal "$(getJSONData "$MCURLJSON" server)" sha1)

LOCAL_FILE=$([[ -n $1 ]] && printf $1 || printf /tmp/$SERVER_JAR_NAME)

if [[ -a "${LOCAL_FILE}" ]]; then
  printf "${LOCAL_FILE} exists -- moving to ${LOCAL_FILE}.old\n"
  mv ${LOCAL_FILE} ${LOCAL_FILE}.old
fi

printf "\nDownloading ${SERVER_JAR_NAME}..."
wget -q -O ${LOCAL_FILE} ${SERVER_URL}
printf "\nFile downloaded at: ${LOCAL_FILE}"

printf "\nChecking sha1sum of ${LOCAL_FILE}..."
DOWNLOAD_FILE_SHA1SUM=$(sha1sum ${LOCAL_FILE} | awk '{print $1}')

if [ $(sha1sum "${LOCAL_FILE}" | awk '{print $1}') != "${SERVER_FILE_SHA1}" ]; then
  printf "\nSHA1 of downloaded file does not match!"
  rm ${LOCAL_FILE}
else
  printf "\nSHA1 matches!\n"
fi

```

This script builds a Spigot server and does more than just drop the jar in /tmp.  I have it setup so it can be called from crontab to update my server automatically...but for a specific version to avoid breaking my plugins.  I never auto-upgrade version numbers because the plugins almost always have to be updated manually.  Plugins can add/remove/change features and permissions nodes so you need to evaluate each one in detail when updating as well as test to make sure the plugins even work.

build-spigot.sh
```

#!/bin/sh
BuildRev="1.12.2"
NewJar="spigot-${BuildRev}.jar"
TargetDir="/opt/spigot/noobserver"
TargetJar="server.jar"
BuildDir="/opt/spigot/build"
cd ${BuildDir}
if [ -f ${BuildDir}/craftbukkit-${BuildRev}.jar ]; then
  echo "Purging old file: ${BuildDir}/craftbukkit-${BuildRev}"
  rm ${BuildDir}/craftbukkit-${BuildRev}.jar
fi
if [ -f ${BuildDir}/${NewJar} ]; then
  echo "Purging old file: ${BuildDir}/${NewJar}"
  rm ${BuildDir}/${NewJar}
fi
if [ -f ${BuildDir}/BuildTools-old.jar ]; then
  echo "Purging old file: ${BuildDir}/BuildTools-old.jar"
  rm ${BuildDir}/BuildTools-old.jar
fi
echo "Archiving existing BuildTools to ${BuildDir}/BuildTools-old.jar"
mv ${BuildDir}/BuildTools.jar ${BuildDir}/BuildTools-old.jar
echo "Getting latest BuildTools..."
wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
echo "Compiling latest Spigot version"
java -jar ${BuildDir}/BuildTools.jar --rev ${BuildRev}
if [ -f ${BuildDir}/${NewJar} ]; then
  echo "Successfully created ${BuildDir}/${NewJar}"
  if [ -f ${TargetDir}/server-old.jar ]; then
    echo "Removing old backup (server-old.jar)..."
    rm ${TargetDir}/server-old.jar
  fi
  echo "Stopping Spigot server to begin upgrade..."
  /var/scripts/prod/stop.sh noobserver UPGRADE 1 fast
  echo "Archiving existing server to server-old.jar..."
  mv ${TargetDir}/server.jar ${TargetDir}/server-old.jar
  echo "Updating server.jar..."
  mv ${BuildDir}/${NewJar} ${TargetDir}/${TargetJar}
  echo "Configuring ownership permissions..."
  chown noobserver:minecraft ${TargetDir}/server.jar
  echo "Starting Spigot server..."
  /var/scripts/prod/start.sh noobserver 4096
fi

```

To start a server in a screen: (substitute "**LowRightsUserName**" for the local user account you created for that session)
```
su LowRightsUserName --command "screen -d -m -S LowRightsUserName -t LowRightsUserName java -d64 -XX:MaxPermSize=256M -Xincgc -Xmx4096 -jar /path/to/server.jar --log-strip-color
```

To send an in-game message to users via the console and then send a carriage return:
```
screen -S LowRightsUserName -p LowRightsUserName -X stuff "say Hello World"
screen -S LowRightsUserName -p LowRightsUserName -X eval "stuff \015"
```

To send the shutdown command to the console to stop the server...and thus the screen session:
```
screen -S LowRightsUserName -p LowRightsUserName -X stuff "stop"
screen -S LowRightsUserName -p LowRightsUserName -X eval "stuff \015"
```


LHammonds

---

