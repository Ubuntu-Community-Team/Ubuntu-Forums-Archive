---
title: "Cat is executing commands"
date: 2013-04-17
forum: Ubuntu Application Development
---

### Post by pedrommone on 2013-04-17
When I try to cat a block and save it, some function are executed, like this one

```
USER_ID=$(mysql -u $DB_USER -p$DB_PASS -h$DB_HOST $DB_NAME --disable-column-names -e "SELECT id FROM users WHERE username='$USER';")
```

My bash is the follow

```

#!/bin/bash


script="tunnel-bootstrap.sh"
temp=`getopt -l id:,name:,ip:,type:,host:,user:,pass:,db: -n "$0" -- '' "$@"` || exit 1
eval set -- optname optval "$temp"
declare -A opt
while shift 2; do
  case $1 in
    --id|--name|--ip|--type|--host|--user|--pass|--db) opt[${1#--}]="$2";;
  esac
done
cat <<EOF >"$script"
#!/bin/bash


############################
# CARREGA DADOS DO SERVIDOR
############################


SERVER_ID=${opt[id]}
SERVER_NAME="${opt[name]}"
SERVER_IP="${opt[ip]}"
SERVER_TYPE="${opt[type]}"
DB_HOST="${opt[host]}"
DB_USER="${opt[user]}"
DB_PASS="${opt[pass]}"
DB_NAME="${opt[db]}"


############################
# INICIO DO CHECK-IN
############################


if [ $USER == "ubuntu" ]; then
        return
fi


trap '' 2


USER_ID=$(mysql -u $DB_USER -p$DB_PASS -h$DB_HOST $DB_NAME --disable-column-names -e "SELECT id FROM users WHERE username='$USER';")
EOF

```

Thanks in advance.

---

### Post by CharlesA on 2013-04-17
This might help...
[http://tldp.org/LDP/abs/html/commandsub.html](http://tldp.org/LDP/abs/html/commandsub.html)

Cat takes anything inside $(...) and expanding it.

---

### Post by schragge on 2013-04-17
+1
Just put a backslash before each dollar sign in the command to prevent expansion:
```

USER_ID=\$(
    mysql -u \$DB_USER -p\$DB_PASS -h\$DB_HOST \$DB_NAME -B -e \
        "SELECT id FROM users WHERE username='\$USER';"
)

```

---

### Post by pedrommone on 2013-04-17
Thank buddies, its working now!

---

### Post by sisco311 on 2013-04-17
-1 :)

cat has nothing to do with the SHELL substitutions. ;)

You are using a `here document'.
Check out: [http://mywiki.wooledge.org/HereDocument](http://mywiki.wooledge.org/HereDocument)
and
```
man bash | less +/"^ +Here Documents"
```


If you want to avoid shell substitution, just quote any character in the delimiter word:
```
cat << \EOF > file
...
EOF

#or
cat << E\OF > file
...

EOF

#or
cat << 'EOF' > file
...
EOF
```

---

### Post by schragge on 2013-04-17
But the OP *needs* parameter expansion inside here-document. That was [thread=2135204]the point[/thread] of using it in the first place.

---

### Post by sisco311 on 2013-04-17
> **schragge said:**
> But the OP *needs* parameter expansion inside here-document. That was [thread=2135204]the point[/thread] of using it in the first place.

Oh, thanks, I missed that. Then yes, escaping the $ sings is the way to go.

---

