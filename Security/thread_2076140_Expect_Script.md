---
title: "Expect Script"
date: 2012-10-25
forum: Security
---

### Post by ApostlePaul on 2012-10-25
Hi Guys,
 
I am trying to create an expect script which will send a different password string based on the "expect"
 
Condition A: If a cisco device has not been setup with a username then the first prompt will simply be "Password:" - then it should use passwordA (no username)
 
Condition B: If it has been setup with a username then the prompt will be "Username:" followed by "Password:" - then it should use Username and PasswordB
 
#!/bin/bash
# Declare host variable as the input variable
host=$1
&#12288;
# Start the expect script
(expect -c "
 
set timeout 20
# Start the session with the input variable and the rest of the hostname
spawn telnet $host
set timeout 3 
if {expect \"Password:\"} {
send \"PasswordA\"}
elseif { expect \"Username:\"}
send \"UsersName\r\"}
expect \"Password:\"
log_user 0 
send \"PasswordB\r\"
log_user 1
expect \"*>\"
# send \"show version\r\"
# set results $expect_out(buffer) 
#expect \"Password:\"
#send \"SomeEnablePassword\r\"
# Allow us to interact with the switch ourselves
# stop the expect script once the telnet session is closed
send \"quit\r\"
expect eof
")

---

