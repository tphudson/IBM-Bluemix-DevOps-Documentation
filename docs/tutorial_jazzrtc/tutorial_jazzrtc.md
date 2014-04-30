#Developing BlueMix applications in Java with Eclipse and DevOps Services

This tutorial shows you how to develop a Java application using BlueMix, DevOps Services and the RTC client for Eclipse.

##Getting your app

We'll start by forking the sample project, [WordCounter] (https://hub.jazz.net/project/pskhadke/WordCounter/overview).This project uses Jazz Source 
Control Management (Jazz SCM for short). It contains a manifest for deploying to Bluemix and can be loaded directly in the RTC client for Eclipse. 
DevOps Services also supports Git projects. To find out more about support for Git, check out the [Getting Started with BlueMix and DevOps Services 
using Java](tutorial_jazzeditorjava/tutorial_jazzeditorjava) tutorial.

Go to the [WordCounter](https://hub.jazz.net/project/pskhadke/WordCounter/overview) project. Click ***EDIT CODE*** to open the Web IDE.

>	![Click Edit Code](images/click_edit_code.jpg)

You can build your own application by clicking the ***FORK*** button and entering a unique name when prompted. You get a new project, a new project 
name and a copy of the code from the sample project.

>	![Fork](images/fork.jpg)

Now that you've forked the project, you'll need to deliver the changes to the Jazz SCM repository. Browse to the Jazz SCM Changes page.

>	![Jazz SCM Changes page](images/jazzscm.jpg)

Click ***Deliver***.

>	![Deliver Changes](images/share.jpg)

##Running your app

You got your project in minutes! That's great! Now, let's set up how it's going to get built and deployed. Go to the deployment page by clicking the 
***BUILD & DEPLOY*** button. Turn on deployment in the advanced mode by clicking the ***ADVANCED*** button. On the Configure Builder page, specify
	
* The password associated with your IBM id as the "Your IBM DevOps Services password"
* The folder containing your code, i.e. "WordCounter" as the "Build script path"
* A name for the "Build archive directory"	

The folder "WordCounter" is the folder that Eclipse uses to represent your project. The "Build archive directory" is where the output war and manifest
for your project will go after a successful build.

Check the "Enable unit tests" checkbox to run test cases during a build. Finally, click ***Save***.

>	![Configure Builder](images/configure_builder.jpg)

Click on ***Deployer*** to open the Configure Deployer page. This page will use the settings provided by the `manifest.yml` file, included as part of
the project. All of the values, except for the hostname, can be used directly as provided. The hostname is used to define your application's url and
needs to be unqiue for each application deployed. Let's override the host with the `-n` option in the `cf push` command as below. Click ***Save*** and
you're all set!

>	![Configure Deployer](images/configure_deployer.jpg)

Click the ***REQUEST BUILD*** button to see your project get built and deployed for the first time. This takes a couple of minutes. And then... the
circle goes green! The app's live!

>	![Successful Build](images/build1_success.jpg)

Click the application link... It works! Awesome!

>	![Application](images/app.jpg)

---
##Accessing your app from the RTC client for Eclipse

Now that you have a running application, let's connect to it from the RTC client for Eclipse. Click on the project link to go to the Project Overview
page. 

>	![Project Link](images/project_link.jpg)

You can get the Jazz Repository information here. 

>	![Team Invitation](images/team_invite.jpg)

The [Setting up Eclipse, Git, and RTC Desktop Clients to access DevOps Services](tutorial_clients/tutorial_clients#jazzscm) tutorial shows you how to
set up the RTC client for Eclipse, connect to your project and load the code.						

---
##Delivering your first change

You're in the RTC client for Eclipse. So, let's change something and see it go live. For example, change the app name on line 10 of index.html.

>	![Edit Code](images/edit_code.jpg)

Next, you'll want to deliver the change to the Jazz SCM repository. To do this, check-in the change in a new Change set using the Pending Changes view.

>	![Check In Change](images/checkin.jpg)

You can edit the comment for the Change set...

>	![Edit Change Set Comment](images/edit_comment.jpg)

And then deliver it. 

>	![Deliver Change Set](images/deliver.jpg)

Visit the deployment page in the browser. A build should get triggered soon. The page gets automatically updated. Wait for it to go green.

>	![Successful Build](images/build2_success.jpg)

You click the app link and voila! The app name's updated! Cool!						

---
##Adding a test failure

Let's add a failure to the JUnit tests so that you can see what happens when the build fails. Set "this.wcFinder" to null on line 23 of 
WordCounterFinderTest.java.

>	![Edit Test Case](images/edit_testcase.jpg)

In addition, change the app name on line 10 of index.html. Deliver the changes.

>	![Edit App Name Again](images/edit_code_2.jpg)

The deployment page shows a failed build, as expected. Note how the build was not deployed automatically. Only successful builds are automatically
deployed. Also note that when you click the app link, the app name is not updated. 

>	![Failed Build](images/build3_failure.jpg)

On the deployment page, click the build to access the logs.

>	![Click Build](images/build_log.jpg)

---
##Fixing the bug

Let's revert the code in WordCounterFinderTest.java to its previous state and deliver the change.

>	![Fix Test Case](images/fix_testcase.jpg)

And our build is back to green! 

>	![Successful Build](images/build4_success.jpg)

So is our app... Great!

>	![Application](images/app3.jpg)
						
That was easy. Now you can develop Java applications on your own. Thanks for following along. And tell us what you think. What did we do well? What can
we do better? Post your comments to our [forum](https://www.ibmdw.net/answers?community=jazzhub)" or send us an [email](mailto:hub_help@jazz.net).

---

##More Tutorials

If you're interested in trying more BlueMix and DevOps capabilities, here is a list of tutorials:

* [Getting Started with BlueMix and DevOps Services using Node.js](tutorial_jazzeditor/tutorial_jazzeditor)
* [Getting Started with BlueMix and DevOps Services using Java](tutorial_jazzeditorjava/tutorial_jazzeditorjava)
* [Setting up Eclipse, Git, and RTC Desktop Clients to access DevOps Services](tutorial_clients/tutorial_clients)
* [Developing BlueMix applications in Node.js with the DevOps Services Web IDE](tutorial_jazzweb/tutorial_jazzweb)
			