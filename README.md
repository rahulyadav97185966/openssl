# openssl (creating a secure shell) #

    1) oc new-project myproject : it creates new project
    2) oc new-app --name=app1 --docker-image=httpd  : it create httpd pod of name app1
    3)  oc get pods -w  : check where the pod and deployment is created or not
    4)  oc get pods  : get all running pods
    5)  oc create sa mysa  : create service account
    6)  oc get sa : it shows the list of all service accounts
    7)  oc adm policy add-scc-to-user anyuid -z mysa : we apply this policy so any user can use it
    8)  oc edit dc app1  : In deployment config we have to edit 
                edit after  termination seconds :
                        ServiceAccountName: mysa
   9)  oc get pods : check the pods are running or not
   10)  oc get svc  : get svc
   11)  curl 172.30.128.18  : check whether the pod is showing index file or not
   12)  oc expose svc app1 : create route so we can access it outside the cluster
   13)  oc get route  : get the link and paste it into browser
   14)  openssl genrsa -out private.key 2048  : generate ssl certificate of private.key
   15)  openssl req -new -key private.key -out example-ca.csr : create example-ca.csr
   16)  openssl x509 -req -days 365 -in example-ca.csr -signkey private.key -out public.crt : create public certificate
   17)  ls  : ls shows all listing directories
   18)  oc get route  : get route and delete it
   19)  oc delete route app1
   20)  oc create route edge --service=app1 --hostname=app1-myproject.2886795276-80-host18nc.environments.katacoda.com --key=private.key --cert=public.crt  : againg create route using above command
   21)  oc get route : get route and paste it and run using https://.....
