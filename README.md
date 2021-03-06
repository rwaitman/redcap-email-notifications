# REDCap Notifications Plugin

### INTRODUCTION
While the email notification code is not strictly a REDCap plugin, the code was
structured as such, since it may end up using a significant amount of what ends
up becoming our generalizable REDCap plugin infrastructure (for more detail see
the REQUIREMENTS section). 

This code enables email notifications to be associate with REDCap projects, and
sent under conditions set in a dedicated notifications REDCap project.  

### REQUIREMENTS
This code requires that the REDCap Hook Registry code be installed.  The hook
registry was developed along side this notification plugin.  More information
about the REDCap Hook Registry can be found at https://github.com/kumc-bmi/redcap-hook-registry.

This plugin's other requirement can all be located within the utils directory.
The development of this plugin has occurred concurrently with the development of
several other REDCap customizations.  Due to this, there is the potential for
the aggregation of common functionality into a generalizable REDCap plugin/hook
infrastructure.  The code that lends itself to this has been placed into the 
utils directory and is the following:

 * `records.php`: This code was originally developed for the RE-POWER counseling
                form plugin in order to interact with the REDCap database.  That
                code has evolved into a simple MVC pattern, and the plan is to 
                pull all generalizable code out into a separate "plugin 
                framework".  The model in the MVC pattern has yet to be fully 
                fleshed out, so functionality provided by `records.php` is
                evolving. 

 * `PluginConfig.php`: This contains a class definition for an immutable object,
                     which implements the PHP array interface and contains
                     configuration option pulled in from an ini file.

 * `RestCallRequest.php`: This code was written by REDCap developer for use with
                        their API, and distributed on the REDCap Consortium site
                        (http://project-redcap.org).

### INSTALLATION
To install this code:
 1. Clone the notification plugin code into `<redcap-root>/plugins/notifications`.
 2. Create a new REDCap project for managing notifications, and upload the 
    `data_dictionary.csv` file in this directory.

### CONFIGURATION
The notification plugin configuration can be found in `notifications.ini`:
 * `notification_pid`: The project id of the notification management project
                     created during installation.
 * `api_url`: The URL to the local REDCap installation's API
            (e.g. http://redcap.kumc.edu/api/).

### MAINTAINERS
Current maintainers:
 * Michael Prittie <mprittie@kumc.edu>
