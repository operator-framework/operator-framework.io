---
title: "Why page"
date: 2020-02-12T15:41:36-03:00
draft: false
menu: 
    main:
        name: FAQ
        weight: 500
---

### HOW ARE OPERATORS CREATED?

The premise of an Operator is to have it be a custom form of Controllers, a core concept of Kubernetes. A controller is basically a software loop that runs continuously on the Kubernetes master nodes. In these loops the control logic looks at certain Kubernetes objects of interest. It audits the desired state of these objects, expressed by the user, compares that to what’s currently going on in the cluster and then does anything in its power to reach the desired state.

This declarative model is basically the way a user interacts with Kubernetes. Operators apply this model at the level of entire applications. They are in effect application-specific controllers. This is possible with the ability to define custom objects, called Custom Resource Definitions (CRD), which were introduced in Kubernetes 1.7. An Operator for a custom app would, for example, introduce a CRD called FooBarApp. This is basically treated like any other object in Kubernetes, e.g. a Service.

The Operator itself is a piece of software running in a Pod on the cluster, interacting with the Kubernetes API server. That’s how it gets notified about the presence or modification of FooBarApp objects. That’s also when it will start running its loop to ensure that the application service is actually available and configured in the way the user expressed in the specification of FooBarApp objects. This is called a reconciliation loop (example code). The application service may in turn be implemented with more basic objects like Pods, Secrets or PersistentVolumes, but carefully arranged and initialized, specific to the needs of this application. Furthermore, the Operator could possibly introduce an object of typeFooBarAppBackup and create backups of the app as a result.
    
### Another FAQ

answer for another FAQ