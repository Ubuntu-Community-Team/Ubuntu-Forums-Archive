---
title: "creating child processes in a script"
date: 2010-10-13
forum: Ubuntu Dev Link Forum
---

### Post by Adz199 on 2010-10-13
hey guys just need a bit of help as im a bit of noob when it comes to Linux and im sorry if this is in the wrong part of the forum but basically im working on a project and getting no where what so ever and i was wondering if i could get your help. Basically i have to create two scripts do:

The parent script, which will:
          o spawn several child processes.
          o keep track of the progress of the child processes.
          o Enable the user to terminate any of the child processes.
          o View all running processes.
          o On exit, terminate all remaining child processes and delete any temporary files.
    * a "helper" script which will periodically write to a temporary file on how long it has been running, including an identifying number saying which instance of the script wrote to the file, and the pid of that process. The helper script will consist of a loop which will run forever which does three things:
          o sleep for a specified period of time;
          o increment a counter variable;
          o Write the number of iterations so far to a temporary file.
      (The helper script will be terminated by the parent.)

The parent script will spawn five instances of the helper script, each with a separate ID (as opposed to a pid) and a sleep value. The sleep values should be different for each instance.

Next, the parent script will print each of the five temporary files, thus reporting on the progress of each child process.

any help you could give me would be greatly appreciated

thanks Adam

---

### Post by amauk on 2010-10-14
I hope this isn't your homework or anything ;)

extremely rough concept of what you've posted

**main**```
#!/bin/bash

SUB_PROCESS_SCRIPT="./sub_process"
NUM_SUB_PROCESSES=5

function output_results
{
    for ((i=0; i<${#SUB_PROCESS_ARRAY[*]}; i++)); do
        echo "Child ${i}: $(cat ${SUB_PROCESS_ARRAY[$i]}.tmp)"
    done
}

function kill_children
{
    for ((i=0; i<${#SUB_PROCESS_ARRAY[*]}; i++)); do
        echo "killing PID ${SUB_PROCESS_ARRAY[$i]}"
        kill ${SUB_PROCESS_ARRAY[$i]}
    done
}

function array_pop
{
    if [ -n "$1" ]; then
        NEW_ARRAY=( )
        for ((i=0; i<${#SUB_PROCESS_ARRAY[*]}; i++)); do
            if [ "$i" -ne "$1" ]; then
                NEW_ARRAY[${#NEW_ARRAY[*]}]=${SUB_PROCESS_ARRAY[$i]}
            fi
        done
        SUB_PROCESS_ARRAY=( )
        for ((i=0; i<${#NEW_ARRAY[*]}; i++)); do
            SUB_PROCESS_ARRAY[${#SUB_PROCESS_ARRAY[*]}]=${NEW_ARRAY[$i]}
        done
    fi
}

SUB_PROCESS_ARRAY=( )

for ((i=0; i<$NUM_SUB_PROCESSES; i++)); do
    $SUB_PROCESS_SCRIPT &
    SUB_PROCESS_ARRAY[${#SUB_PROCESS_ARRAY[*]}]=$!
done


INPUT=""

output_results
while [ "$INPUT" != "Q" ]; do
    echo "----"
    echo "Choose an action"
    echo "T [Terminate a child process]"
    echo "R [Refresh results]"
    echo "Q [Quit]"

    read INPUT

    case $INPUT in
    "T")
        output_results
        echo "Which child to terminate?"
        read KILL_CHILD
        echo "killing PID ${SUB_PROCESS_ARRAY[$KILL_CHILD]}"
        kill ${SUB_PROCESS_ARRAY[$KILL_CHILD]}
        echo "Delete PID tmp file? [y/n]"
        read DEL_TMP
        if [ "$DEL_TMP" == "y" ]; then
            rm -f "${SUB_PROCESS_ARRAY[$KILL_CHILD]}.tmp"
        fi
        array_pop $KILL_CHILD
        ;;
    "R")
        output_results
        ;;
    "Q")
        ;;
    esac
done
kill_children
```

**sub_process**```
#!/bin/bash

while [ true ]; do
    echo "I am PID $$, and I've been running for $SECONDS seconds" > $$.tmp
    sleep 10
done
```

---

### Post by Adz199 on 2010-10-14
wow thanks so much nah its more of a project im trying to get this right so then i can get more hardcore with child processes do some real fun stuff:)

---

