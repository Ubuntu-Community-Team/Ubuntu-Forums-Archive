---
title: "Send/receive SMS via android device."
date: 2013-04-29
forum: Server Platforms
---

### Post by szafran on 2013-04-29
Hi,

I have a spare Samsung Gio android device.
On my NAS server I have Ubuntu Server 12.04.2 installed.
I'm redirecting all root mail to my e-mail on gmail using /root/.forward - this works fine, and I'd like to keep that.
I'd like to add to that sending SMS to specified number(s) containing mail's subject and/or body (it would be nice to have a choice on what to send, eg. just subject, or subject+body).

To that I'd like to make some kind of remote controlling device from that phone.
Eg. I send to it a SMS: "NAS:reboot", and it'll reboot the machine (after checking that the SMS came from a number that's on a predefined whitelist).

Best regards
Szafran

---

### Post by szafran on 2013-04-30
Ok. So after some hours (about 12 or so ;) ) of tests and research I have a working script that sends SMS messages.
The script requires that ShellSMS needs to be installed on the phone ([https://play.google.com/store/apps/details?id=it.elaware.shellsms](https://play.google.com/store/apps/details?id=it.elaware.shellsms)), and adb on the PC.
It scans a directory for *.sms files, and sends what's in them to specified phone number using above apps.

The script:
```
#!/bin/bash

#wymaga zainstalowania ShellSMS na telefonie, podlaczenia przez USB i wlaczenia Debugowania USB


#parametry
PLIK_USTAWIEN="`dirname $(readlink -f $0)`/`basename $0`.settings"
KATALOG_KOLEJKI_SMSOW="/home/szafran/.scripts/smsy/kolejka"
HASLO_DO_SHELLSMS="1234567890"




#procedura usuwajaca biale znaki
TRIM()
{


  local var="$1"
  var="${var#"${var%%[![:space:]]*}"}"  # remove leading whitespace characters
  var="${var%"${var##*[![:space:]]}"}"  # remove trailing whitespace characters
  echo -n "$var"


} #TRIM






#glowna petla
while :;
do


  #odczytujemy ustawienia kopii zapasowych z pliku .settings
  i=0
  while read LINIA
  do
    LINIA=`TRIM "$LINIA"`
    [[ "$LINIA" =~ ^#.*$ ]] && continue
    [[ "$LINIA" == "" ]] && continue
    SETTINGS[i++]="$LINIA"
  done < "$PLIK_USTAWIEN" #while read LINIA
  unset i
  unset LINIA


  NR_TELEFONU="${SETTINGS[0]}"
  POCZATEK_CISZY_NOCNEJ=${SETTINGS[1]}
  KONIEC_CISZY_NOCNEJ=${SETTINGS[2]}
  MAIN_SLEEP=${SETTINGS[3]}
  NIGHT_SLEEP=${SETTINGS[4]}


  unset SETTINGS


  #sprawdzamy czy aktualna godzina jest poza ustawionymi godzinami ciszy nocnej
  #jesli tak to wysylamy smsmy, jesli nie to pomijamy
  AKTUALNA_GODZINA=$( date +%H )


  if [ $AKTUALNA_GODZINA -lt $POCZATEK_CISZY_NOCNEJ ] && [ $AKTUALNA_GODZINA -gt $KONIEC_CISZY_NOCNEJ ]; then


    #sprawdzamy czy sa jakies smsy w kolejce do wyslania - jesli tak to interesuje nas tylko najstarszy plik
    PLIK_KOLEJKI=$( find "$KATALOG_KOLEJKI_SMSOW" -type f -iname "*.sms" -printf '%T@ %p\n' | sort -k 1n | sed 's/^[^ ]* //' | head -n 1 )


    if [ -n "$PLIK_KOLEJKI" ]; then


      TRESC_WIADOMOSCI=$( cat "$PLIK_KOLEJKI" )
      TRESC_WIADOMOSCI=$( TRIM "$TRESC_WIADOMOSCI" )
      TRESC_WIADOMOSCI="${TRESC_WIADOMOSCI//$'\r'/$'. '}"
      TRESC_WIADOMOSCI="${TRESC_WIADOMOSCI//$'\n'/$'. '}"


      #wysylamy smsa z kolejki
      WYNIK=$( adb shell am startservice -a sendsms -n it.elaware.shellsms/.sms -e phonenumber "$NR_TELEFONU" -e smsbody "$TRESC_WIADOMOSCI" -e password "$HASLO_DO_SHELLSMS" )


      echo "$WYNIK" | grep -i -q "error"
      if [ $? -ne 0 ]; then
        rm -f "$PLIK_KOLEJKI" &> /dev/null
      fi #if [ $? -ne 0 ]; then


    fi #if [ -n "$PLIK_KOLEJKI" ]; then


    unset PLIK_KOLEJKI


    #uspienie pomiedzy kolejnymi iteracjami petli glownej
    sleep $MAIN_SLEEP


  else #if [ $AKTUALNA_GODZINA -gt $POCZATEK_CISZY_NOCNEJ ] || [ $AKTUALNA_GODZINA -lt $KONIEC_CISZY_NOCNEJ ]; then


    #uspienie pomiedzy kolejnymi iteracjami petli glownej w czasie ciszy nocnej
    sleep $NIGHT_SLEEP


  fi #if [ $AKTUALNA_GODZINA -gt $POCZATEK_CISZY_NOCNEJ ] || [ $AKTUALNA_GODZINA -lt $KONIEC_CISZY_NOCNEJ ]; then


done #while :;


exit 0
```

.settings file:
```
+48111222333
21
8
3
120
```

What needs to be setup to use it:
KATALOG_KOLEJKI_SMSOW - this is the directory that contains the *.sms files (the sms queue)
HASLO_DO_SHELLSMS - this is the password that you setup in ShellSMS on your phone

.settings file lines:
1: phone number including country code
2: night time hours start
3: night time hours end
4: day time script sleep seconds
5: night time script sleep seconds

The script won't send any messages dusring night time hours. It will send the SMS queue right after the night time ends.
If you name the script file eg. "SMSsender" then the .settings file needs to be named "SMSsender.settings" and placed in the same directory as the script.

And now, does anyone have any idea on how to achieve the rest from my first post ?

---

### Post by szafran on 2013-04-30
After endless tests to get procmail working on my config I gave up.
I've setup mail -> python script redirection in /etc/aliases.
The redirection points to this script:

```
#!/usr/bin/pythonimport sys
import email
import uuid
from time import localtime, strftime


#generujemy unikatowa nazwe pliku
PLIK = str(uuid.uuid4()) + '.sms'


#wczytujemy dane maila przekazane przez alias
full_msg = sys.stdin.readlines()


#przetwarzamy dane maila
msg = email.message_from_string("".join(full_msg));
#mail_to = msg['to']
#mail_from = msg['from']
mail_subject = msg['subject']
#mail_body = msg['body']


#generujemy aktualna date w formacie dla smsa
DATA = strftime("[%Y-%m-%d][%H:%M:%S] ", localtime())

myFile = open('/home/szafran/.scripts/smsy/kolejka/' + PLIK, 'w')
myFile.write( DATA + mail_subject )
myFile.close()
```

So, now I have a working mail to sms queue to sms scripts.
Does anyone know how to read sms messages from the phone ?

---

### Post by tgalati4 on 2013-04-30
You would have to write a custom Android app that scans the SMS inbox and acts on certain messages.  There might be something in the store, but you would have to search through several pages of SMS results.  Sounds like another dozen hours.

---

### Post by szafran on 2013-05-01
Got it :D

4 files on this one:
"script"
"script.commands"
"script.whitelist"
"script.log"

"script" is the script with whatever name you give it
```
#!/bin/bash

#params
BASEFILE="`dirname $(readlink -f $0)`/`basename $0`"
FILE_COMMANDS="$BASEFILE.commands"
FILE_WHITELIST="$BASEFILE.whitelist"
FILE_LOG="$BASEFILE.log"
DELETE_SMSes=0
PAUSE=5

unset BASEFILE

#function that removes white spaces
TRIM()
{

  local var="$1"
  var="${var#"${var%%[![:space:]]*}"}"  # remove leading whitespace characters
  var="${var%"${var##*[![:space:]]}"}"  # remove trailing whitespace characters
  echo -n "$var"

} #TRIM

#finction that writes to the log
LOGIT()
{

  read IN
  if [ "$IN" != "" ]; then

    echo "["`date +"%Y-%m-%d %H:%M:%S"`"]:  $IN" >> "$FILE_LOG"

  fi #if [ "$IN" != "" ]; then

} #LOGIT



#main loop
while true;
do

  #read available commands from .commands file
  unset COMMANDSin
  unset COMMANDSout
  declare -a COMMANDSin
  declare -a COMMANDSout
  index=0
  while read LINE
  do
    LINE=`TRIM "$LINE"`
    [[ "$LINE" =~ ^#.*$ ]] && continue
    [[ "$LINE" == "" ]] && continue
    COMMANDSin[$index]=$( echo "$LINE" | awk -F ';' '{print $1}' )
    COMMANDSout[$index]=$( echo "$LINE" | awk -F ';' '{print $2}' )
    COMMANDSin[$index]=$( TRIM "${COMMANDSin[$index]}" )
    COMMANDSout[$index]=$( TRIM "${COMMANDSout[$index]}" )
    COMMANDSin[$index]=$( echo "${COMMANDSin[$index]^^}" )
    index=$(($index+1))
  done < "$FILE_COMMANDS" #while read LINE
  unset index
  unset LINE

  #read phone whitelist file
  PHONE_WHITELIST=""
  i=0
  while read LINE
  do
    LINE=`TRIM "$LINE"`
    [[ "$LINE" =~ ^#.*$ ]] && continue
    [[ "$LINE" == "" ]] && continue
    PHONE_WHITELIST="$PHONE_WHITELIST"" $LINE"
  done < "$FILE_WHITELIST" #while read LINE
  unset i
  unset LINE

  PHONE_WHITELIST=$( TRIM "$PHONE_WHITELIST" )

  if [ ! -z "$COMMANDSin" ] && [ ! -z "$COMMANDSout" ] && [ ! -z "$PHONE_WHITELIST" ] && [ ${#COMMANDSin[@]} -eq ${#COMMANDSout[@]} ]; then

    #get one unread message from the phone
    RESULT=$( adb shell "sqlite3 /data/data/com.android.providers.telephony/databases/mmssms.db \"SELECT _id, address, body FROM sms WHERE read=0\"" | head -n 1 )

    if [ "$RESULT" != "" ]; then

      SMS_ID=$( echo "$RESULT" | awk -F '|' '{print $1}' )
      SMS_ID=$( TRIM "$SMS_ID" )
      SMS_PHONENO=$( echo "$RESULT" | awk -F '|' '{print $2}' )
      SMS_PHONENO=$( TRIM "$SMS_PHONENO" )
      SMS_BODY=$( echo "$RESULT" | awk -F '|' '{print $3}' )
      SMS_BODY=$( TRIM "$SMS_BODY" )
      SMS_BODY=$( echo "${SMS_BODY^^}" )

      #mark the sms as read on the phone
      adb shell "sqlite3 /data/data/com.android.providers.telephony/databases/mmssms.db \"UPDATE sms SET read=1 WHERE _id=$SMS_ID\"" > /dev/null

      #if the read messages should be removed then do it
      if [ $DELETE_SMSes -gt 0 ]; then

        adb shell "sqlite3 /data/data/com.android.providers.telephony/databases/mmssms.db \"DELETE FROM sms WHERE read=1\""

      fi #if [ $DELETE_SMSes -gt 0 ]; then

      #check if the sms source number is on the whitelist
      #if it is then execute the command
      echo "$PHONE_WHITELIST" | grep -q -i "$SMS_PHONENO"
      if [ $? -eq 0 ]; then

        COMMANDS_NUMBER=${#POLECENIAin[@]}
        for ((index=0; index<$COMMANDS_NUMBER; index++));
        do

          if [ "${COMMANDSin[$index]}" == "$SMS_BODY" ]; then

            ${COMMANDSout[$index]} 2>&1 | LOGIT
            break 1

          fi

        done #for ((index=0; i<$COMMANDS_NUMBER; index++));

      fi #if [ $? -eq 0 ]; then

    fi #if [ ! -z "$COMMANDSin" ] && [ ! -z "$COMMANDSout" ] && [ ! -z "$PHONE_WHITELIST" ]; then

  fi #if [ "$RESULT" != "" ]; then

  sleep $PAUSE

done #while true;

exit 0
```
 
variables:
DELETE_SMSes - if this one is non 0 then the script deletes ALL read messages
PAUSE - pause time between iterations of the main loop


.commands keeps pairs "sms command";"os shell command"
```
#commands format:
#SMS|Shell command
#
#commands sent in sms are case insentitive

reboot;reboot
hello;echo "hello" | wall
```

so if you send sms "hello" then the script executes `echo "hello" | wall`

.whitelist keeps a list of allowed numbers (messages from other number wont do anything)
```
##phone whitelist

+48111222333
```


and the .log filename explains itself.

I've tested this a few times and it worked fine.

I think this concludes this monologue.If anyone has any ideas then please post them.

---

### Post by InnocentCucumber on 2013-07-11
I read all your monologue, except the code part, and conclude that you could probably save my day and be my hero ^^. 
This was before i tryed to decrypt your code and comments. 
I will come back later if i definitly don't find a working solution, and try to learn your native language:(. 
i hope this day a translated version of your code will be posted ^^

---

### Post by szafran on 2013-07-12
@up
done ;)

---

