Kubernetes is gaining prominence for production workloads but how do you explore operational concerns like backup and restore. 

Enter. Kasten K10 (https://www.kasten.io)
* Backup / Recovery
* Disaster Recovery
* Application Mobility


I have created a lab environment on my laptop to support K10. This environment leverages Rancher Desktop https://rancherdesktop.io for the Kubernetes installation.

Rancher Desktop:
Container Management and Kubernetes on the Desktop
An open-source desktop application for Mac, Windows and Linux. Rancher Desktop runs Kubernetes and container management on your desktop. You can choose the version of Kubernetes you want to run. You can build, push, pull, and run container images using either containerd or Moby (dockerd). The container images you build can be run by Kubernetes immediately without the need for a registry.


The goal was to create desktop/ laptop self-contained Kubernetes environment and deploy Kasten to explore its features and use cases. Familiarity and mastery of its interface as well. 


Equipment: 
* Macbook Pro 14"  M1 Max
* 64 Gb RAM
* 2 TB Storage

You might be able to do it with less resources YMMV

Software:
Rancher Desktop
Kasten K10
Homebrew
Helm - MacOS installation


Overview installation:
1. Install Homebrew 3.4.2  https://brew.sh/2021/02/05/homebrew-3.0.0/
  * /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

2. Install Helm for MacOS 
 * **_brew install helm_**

3. Install RancherDesktop
 * https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.1.1/Rancher.Desktop-1.1.1.aarch64.dmg
  * Configure Context for Kubernetes
  * Kubernetes Contexts: rancher-desktop
  * Configure Resources to allocated to RancherDesktop 
  * I used 32gb RAM and 6 CPU
  * ![image](https://user-images.githubusercontent.com/20669209/159422104-8c2a526f-0d03-4c53-8199-460fa710643a.png)

Verify your k3s (kubernets nodes are ready)


****❯ kubectl get nodes
NAME                   STATUS   ROLES                  AGE   VERSION
lima-rancher-desktop   Ready    control-plane,master   44s   v1.22.7+k3s1****
  
 4. Install Kubernees cli for MacOS
  * **_brew install kubernetes-cli_**

5. Install Kasten K10
  https://docs.kasten.io/latest/install/other/other.html

_helm install k10 kasten/k10 --namespace=kasten-io_



Here is the installation of Kasten K10 running a created backup policy for a Auto-Discovered Application. 
![image](https://user-images.githubusercontent.com/20669209/159423709-141e56cb-2f55-4612-8c39-1691f1ea77ca.png)


