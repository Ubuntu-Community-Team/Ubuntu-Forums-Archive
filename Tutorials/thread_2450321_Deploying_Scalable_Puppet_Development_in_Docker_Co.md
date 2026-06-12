---
title: "Deploying Scalable Puppet Development in Docker Containers"
date: 2020-09-11
forum: Tutorials
---

### Post by EuclideanCoffee on 2020-09-11
Docker is a tool that allows you to build a container from an existing template called image. The template comes with software installed and directories configured. Without going on about the technicalities, docker provides the system administrator an easy way to build many virtual computers without touching VNC, spice, or a kvm controller.

 Your first step is to install docker on the server you wish to use to serve all your containers. It may be tempting to use your existing distribution’s packages, but docker always recommends that you download from source.

We're not reviewing how to install docker. This can be found on their home website: [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)


  Once you’ve downloaded docker, you will need to do little configuration. I recommend that you place all users of docker in a group and allow them to execute docker commands. Docker provides instructions here.


  After you’ve logged out and logged into your environment, you should consider configuring proxy. This is a very common search query. All that is needed is a json file inside the docker user’s home directory. Proxy configurations found here.


  Now that docker is installed and configured, you should pull your base image. 

In this tutorial, we’re pulling ubuntu:bionic. Then we’re going to create an agent template inside our puppet infrastructure network.


  To create your first container, first we need an image. We pull it from dockerhub. Then we create a container using it. Next we attach it to make our changes.

  
```

$ docker pull ubuntu:bionic$ docker create -t -i ubuntu:bionic bash
 6d8af538ec541dd581ebc2a24153a28329ac
$ docker start 6d8af538ec541dd581ebc2a24153a28329ac

```


  Next you will see your terminal prompt change. You’re inside the container’s shell. From here we can update and install puppet.

  ```

# apt update
# apt install puppet

```


  Now that puppet is installed on your docker container. Configure your server name and hostname in their respective fields. See mine as an example.

  Inside /etc/hosts, I’ll put attach the Puppet server’s IP address.

  
```

# vim /etc/hosts...4.5.6.7 puppet...

  
```

Next I need to add the server name to puppet.conf.

  ```

# vim /etc/puppet/puppet.conf
... server = abc.example.com ...

```


  Before we run puppet however, we are going to save this to a new template called an image. We do this by leaving the container carefully. If you exit or turn off the container, the image is lost.


  With your ctrl key, hit CTRL + P and then CTRL + Q. You’re now prepared to commit the save to your image.

  
```

$ docker commit 6d8af538ec541dd581ebc2a24153a28329ac puppet-agent

  
```

Once you’ve saved puppet to an image, it’s time to start your first puppet agent. Run puppet agent manually. Then sign the signature request from the Puppet server, assign it a node, and you’re set to begin testing your Puppet node.

  
```

# puppet agent -t

  
```

In the future, you can build new containers from your puppet agent. So instead of using Ubuntu, do the following.

  
```

$ docker create -t -i puppet-agent bash

       
```

---

