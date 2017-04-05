To use Instant Login with Azure AD/Office 365, you'll need to make sure you have:

Active SIS sync with Clever
Azure Active Directory Premium OR Azure Active Directory and PowerShell Proficiency
Not sure if you have Azure Active Directory? If you have a paid subscription to Office 365 for your organization, you have a free subscription to Azure Active Directory.

Preparing for Setup with Clever

If you haven't finished signing up for a Clever account yet, you can choose Google to start. Once you have access to the Clever Admin Dashboard, take the following steps:

Under Instant Login in your Clever dashboard menu, click ‘Settings.'
Choose the shortname for your Instant Login portal URL. The URL will be www.clever.com/in/shortname. Remember to use something that your students and teachers will remember easily.
Keep Identity System set to whatever you already have, or select "Google" for now
Add the contact information for whom students and teachers should reach out to if they have trouble with logging in to Clever - this should be someone who can help them reset their Azure credentials and/or make sure they are shared with the application they're trying to access through Clever.
Click Save
Setup In Azure AD

You'll need to configure Azure Active Directory to connect with Clever Instant Login. In order to do that, you'll need to:

Add the Clever app to Azure Active Directory
Set up SSO to the Clever App
Set up Claims Rules to allow Clever to match Azure users to Clever records
Assign users to the Clever App in Azure AD
Adding the Clever App to Azure AD

Log in to Azure
In the left sidebar, scroll down and click the Active Directory icon: 
Click the arrow next to your directory name: 


Click "Applications" in the options at the top of the page

Click the "Add" button at the bottom of the screen to add a new application.
Choose "Add an application from the gallery" in the window that pops up
Type "Clever" into the search box in the upper-right corner and click the Clever icon to add the application

 

Setting up Azure SSO to Clever

If you've followed the steps above, you should automatically be directed to the Clever App Management page. If not, you can also access this page by navigating to the list of applications in Azure (Active Directory -> Click your Directory -> Click the Applications header) and clicking on the arrow next to the name of the Clever app.



To get started, click on the "Configure single sign-on" button!
Select "Microsoft Azure AD Single Sign-On" from the options provided to allow users to use their Office 365 / Azure AD credentials to sign in to Clever to be taken to the Configure App Settings page

Enter your Clever Portal URL as the Sign On URL - this should follow the format: https://clever.com/in/<your custom shortname>
Click the arrow to move to the next page

Click to download the metadata file, then check the box to confirm that you're all set!
 

Set up Claims Rules

From the Clever Application Management Screen, click the "Attributes" header at the top. Here's an example of what this should look like:



The first four rules in the example should be there by default and should not be changed. The last two are an example of what a claims rule should look like. 

Claims rules are used to allow Clever to determine which student or teacher is logging in. To do this, we match Azure AD attributes to data in Clever. In order for users to be able to log in, there needs to be an attribute for each user type that exactly matches data in a field in Clever. 

Once you have that, you can click the green "Add User Attribute" button to add a new claims rule. 

The "Attribute Name" should be name of the field in Clever. It always follows the format clever.<user type OR 'any'>.<field name>. You can see which fields are available for each user type by browsing your Clever data. If you click on a record, the detail view will show you the name of the fields. Some common Clever fields are:

clever.any.email (will match against email addresses for students, teachers, and admins)
clever.student.student_number
clever.teacher.sis_id
If you have any questions about claims rules, please feel free to reach out to our support team - we'd be happy to help you find the right rules!

 

Assign Users to Clever

From the Clever App Management page, click the "Assign account" button OR click the 'Users' tab in the header. 

In order for Instant Login to work with Azure AD / Office 365, all users that will be logging in through Clever need to be added to the application on this screen. If you have Azure Active Directory premium, you can assign Groups to an app - we recommend assigning users to a Clever group and then giving the Clever group access.

If you do not have Azure Active Directory premium, there is a PowerSchell Client for Azure AD and scripts you can use to bulk add users to an application. Clever is not able to assist with bulk adding users or troubleshooting any issues that may arise from using these scripts.

 

Finalizing Setup with Clever Support

Once you've finished the above, please reach out to Clever Support, and send us your metadata file. We'll finalize the setup on our end!
