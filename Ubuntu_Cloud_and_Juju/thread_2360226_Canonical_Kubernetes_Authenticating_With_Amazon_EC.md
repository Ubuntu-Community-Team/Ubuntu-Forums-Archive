---
title: "Canonical Kubernetes: Authenticating With Amazon EC2 Container Registry"
date: 2017-05-02
forum: Ubuntu Cloud and Juju
---

### Post by kurr on 2017-05-02
I've recently installed The Canonical Distribution of Kubernetes into AWS and I'm to the point where I want to launch pods with containers that live in Amazon's EC2 Container Registry.  The [Kubernetes docs gives guidances on how to do that]("https://kubernetes.io/docs/concepts/containers/images/#using-aws-ec2-container-registry"), but I've been unsuccessful.  I've given the EC2 instances the proper Roles but I'm still having issues pulling down images.  The Canonical Distribution seems to be a different beast than other distros, mainly because JuJu is in the mix.  Can anyone point me to working instructions on how to authenticate against ECR?  I'd also be grateful for help on how to ensure the kublets are running with the ***--cloud-provider=aws*** flag.

Thanks,
Ron

---

