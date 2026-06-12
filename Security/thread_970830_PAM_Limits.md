---
title: "PAM Limits"
date: 2008-11-04
forum: Security
---

### Post by Baversjo on 2008-11-04
Hello! I am using ubuntu server and I have a problem regarding PAM limits. The group I would like to limit is the group "ssh", only one session of each user in the ssh group should be able to be logged in at the same time. I'm able to do this in the file limits.conf but the problem is that I want to disconnect the old user session if a new user session was started with the same username. Now, when a user is for example disconnected from their internet connecton the user stays logged in at my server and I manually need to kill the process for them to be able to login again. Someone know a solution on how I can do this disconnect the old user when the new connects? Worth to note is also that I'm using scponly for the group ssh.

---

### Post by lavinog on 2008-12-13
Why not let them have 2 sessions?

---

### Post by Baversjo on 2009-07-30
> **lavinog said:**
> Why not let them have 2 sessions?

account sharing...

---

### Post by lavinog on 2009-07-30
I am thinking a script could could work.

One approach:
every couple of mins, check for a second ssh connection, if it exists kill the older one.
It won't immediately drop the old connection, but it should be enough to prevent sharing an account.

Would it be acceptable for a user to have two connections from the same ip address?
I don't know what kind of things your users would be doing, but I find using more than one connection to be very handy.

```

> who --ips
someuser pts/0        2009-07-30 21:57 99.66.333.111
someuser pts/3        2009-07-30 21:36 55.66.777.888

> pkill -f 'sshd: someuser@pts/3'
> who --ips
someuser pts/0        2009-07-30 21:57 99.66.333.111

```

---

### Post by lavinog on 2009-07-31
I wrote a script that can do what I mentioned:
```
#!/usr/bin/env python
'''Kill multiple connections'''

# CONFIG VARIABLES
# list of users that should not be killed
NO_KILL_USERS = ['admin_name','other_user_name']

PTS_ONLY = True     # set to False to kill TTY terminals also
SAME_IP_OK=False    # set to True to allow multiple connections from same ip
KILL_LOCAL=False    # set to True to kill users connected to local machine
KILL_SCREENS=False    # set to True to kill users in an attached screen

QUIET=False
LOOP=False
SIMULATE=False



#------------------------------------------

import subprocess
import time
import sys

if '-q' in sys.argv : QUIET=True
if '-l' in sys.argv : LOOP=True
if '-t' in sys.argv : SIMULATE=True
def getwho():
    args=['who','--ips']
    s=subprocess.Popen(args, stdout=subprocess.PIPE )
    output = s.communicate()[0]
    return output
    
def make_who_list(who_strs):
    who_list=[]
    for l in who_strs.split('\n'):
        if len(l)>0:
            who_list.append(l.split() )
    return who_list

def find_killable_connections(who_list):
    #remove users we don't want to kill
    kill_list=[]
    who_list = [ l for l in who_list if l[0] not in NO_KILL_USERS ]

    if KILL_LOCAL == False:
        who_list=[l for l in who_list if ':0' not in l[4]]
    
    if KILL_SCREENS == False:
        who_list=[l for l in who_list if ':S' not in l[4]]
    
    if PTS_ONLY:   # remove non pts connections
        who_list=[l for l in who_list if l[1][0:4] == 'pts/']
    
    # make list of users
    users = [ l[0] for l in who_list ]
    
    # convert to set of users with more than one connection
    users = set( [ u for u in users if users.count(u) > 1 ] )
    
    for user in users:
        # get list of connections from user
        usercons = [ con for con in who_list if con[0]==user ]
        
        # sort usercons by date time (older first) (pts/0 can be newer or older than pts/1)
        usercons.sort( lambda x,y : cmp( x[2:4], y[2:4] ) )
        
        # get most recent connection
        latest_con=usercons.pop()
        latest_ip=latest_con[4]
        
        while len(usercons)>0:
            connection=usercons.pop()
            
            if SAME_IP_OK:
                if connection[4]==latest_ip : continue

            kill_list.append(connection)
    return kill_list
            

def killcon(connection):
    #pkill -f 'sshd: someuser@pts/#'
    pstr='sshd: ' + connection[0] + '@' + connection[1]
    args = ['pkill','-f', pstr ]
    s = subprocess.Popen( args,stdout=subprocess.PIPE)
    


def main():

    while True:
        who = getwho()
        
        if not QUIET:
            if len(who)>1 : print(who)

        who_list = make_who_list(who)
        
        who_to_kill = find_killable_connections(who_list)
        
        for connection in who_to_kill:
        
            if not QUIET:
                #pstr='sshd: ' + connection[0] + '@' + connection[1]
    
                kstr='Killing %s' % ' '.join(connection)
                if SIMULATE:
                    print('SIMULATED: ' + kstr)
                else:
                    print(kstr)
            if not SIMULATE:
                killcon(connection)

        if not LOOP : break
        time.sleep(60)

if __name__== '__main__' : main()


```


Replace admin_name with your user name so your connections wont be killed:
```

# list of users that should not be killed
NO_KILL_USERS = ['admin_name','other_user_name']

```

save the above script to a filename with a .py extension
chmod the file to prevent modification by other users
-t will simulate killing connections
-q will supress output
-l enables the loop (on a 60 second interval)

one way to use this is with the screen program
run screen, then run the script with the loop switch
press ctrl-a then press d. This will detach the screen but continue running the script
to go back to the screen the script was running on use screen -r

Note: the script can't kill users that are attached to a screen...yet.

[s]Most likely there is a better way to do this. I have to do some research but I think there is a way to execute a script when a user logs in.
.bashrc would be the easy way, but the user has permissions to modify it.[/s]
Edit: /etc/profile lets you run commands when bash is loaded.

---

