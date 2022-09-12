# Rest-API-using-Spring-boot

In configureGlobal() method, we have added two users: One user with “ROLE_USER” role and another user with both “ROLE_USER” and “ROLE_ADMIN” roles. That means this second user will act as a Admin User. Like this we can configure any number of users and roles.
We can use either authorities(ROLE) or roles(ROLE) methods to configure Roles in our application.
Difference between authorities() and roles() methods:
authorities() needs complete role name like “ROLE_USER”
roles() needs role name like “USER”. It will automatically adds “ROLE_” value to this “USER” role name.
In configure() method, we have defined different URLs with required Access Roles.
antMatchers("/homePage")
   .access("hasRole('ROLE_USER') or hasRole('ROLE_ADMIN')")
This code snippet configures that “/homePage” is available for both USER and ADMIN Roles.

 .antMatchers("/userPage").access("hasRole('ROLE_USER')")
 .antMatchers("/adminPage").access("hasRole('ROLE_ADMIN')")
This code snippet configures that “/userPage” is accessible by “USER” role only and .“/adminPage” is accessible by “ADMIN” role only. If other roles access these pages, we will get access “403 Access is Denied” Error message.
