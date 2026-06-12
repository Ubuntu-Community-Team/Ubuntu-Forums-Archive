---
title: "HOWTO: run Atlassian Bamboo Agent under upstart"
date: 2011-02-16
forum: Server Platforms
---

### Post by benw01 on 2011-02-16
This HOWTO installs bamboo agent into /usr/local/bamboo-agent, and configures upstart to supervise it and start it at boot time.

Tested on Ubuntu 10.04LTS only. Should work on 10.10 as well, I believe.

NOTE: This uses Sun's Java JDK, not the JRE. On the machine I was setting up, the JDK was required for other uses, so I haven't tested it under the JRE.

**1. Install Sun's Java JDK**
Uncomment the "partner" lines in /etc/apt/sources.list.
Run the following in a terminal, as root:
```

apt-get update
aptitude -R install sun-java6-jdk

```

**2. Install the agent's jar file**
Run the following in a terminal, as root:
```

mkdir -p /usr/local/bamboo-agent
cd /usr/local/bamboo-agent
wget [http://your-bamboo-server.example.com/admin/agent/bamboo-agent-2.6.1.jar](http://your-bamboo-server.example.com/admin/agent/bamboo-agent-2.6.1.jar)
ln -s bamboo-agent-2.6.1.jar bamboo-agent.jar

```

**3. Create a non-root user to run bamboo**
Run the following in a terminal, as root:
```

useradd -c "Bamboo Agent User" -d /usr/local/bamboo-agent bamboo
chown -R bamboo:bamboo /usr/local/bamboo-agent

```

**4. Configure bamboo-agent in upstart**
Run the following in a terminal, as root:
```

cat > /etc/init/bamboo-agent.conf<<EOF
# bamboo-agent - Continuous Integration tool
#
# Bamboo is a Continuous Integration tool.
# Required-Start:       
# Required-Stop:        

description "Bamboo continuous integration agent"

start on runlevel [2345]
stop on runlevel [!2345]

# Give up if restart occurs 10 times in 30 seconds.
respawn limit 10 30

chdir /usr/local/bamboo-agent

exec sudo -u bamboo /usr/bin/java -jar /usr/local/bamboo-agent/bamboo-agent.jar [http://your-bamboo-server.example.com/agentServer/](http://your-bamboo-server.example.com/agentServer/)
respawn
EOF

```

** 5. Start 'er up!**
Run the following in a terminal, as root:
```

start bamboo-agent

```

---

