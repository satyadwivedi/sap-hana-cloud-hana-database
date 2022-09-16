<!-- loio7f681c32c2a34735ad85e4ab403f8c26 -->

# Getting Started with Multitarget Application Development in Cloud Foundry on SAP BTP

Multitarget applications running in Cloud Foundry on SAP Business Technology Platform \(SAP BTP\) must include a number of mandatory files that are used for configuration and deployment.

To set up your SAP HANA Cloud application as a multi-target application, you need to create the necessary source files and place them in the appropriate folders. On deployment, the SAP HANA Cloud deployment service reads the information contained in the various configuration files and uses it to deploy the various application components to the corresponding targets.

The following high-level rules need to be followed when setting up your SAP HANA Cloud application:

-   Separate all database content \(design-time representations of tables, views, procedures, etc.\)
-   Isolate all static content \(HTML, images, other UI related files\) in its own folder.
-   Place language-specific application source files in their own folder.

    Since `XSODATA` service files must be deployed to a JavaScript or Java run-time, place OData service definitions in the application source folders, for example, `javascript/odata/` or `java/odata/`.


> ### Note:  
> The `XSODATA` infrastructure for OData services based on OData version 2 will no longer be extended or improved. In addition, `XSODATA` does not support SAP HANA Cloud services, as described in SAP note: [3013788](https://launchpad.support.sap.com/#/notes/3013788). For new OData services, it is recommended to move to OData version 4 or, alternatively, switch to the new SAP Cloud Application Programming \(CAP\) model. For more information, see *Related Information* below.

-   `db/`

    Contains only database artifact, for example: tables, views stored procedures, etc.

-   `web/`

    Static HTML resources

-   `java/`

    Java source code and any Odata service definitions

-   `javascript/` or `js/`

    JavaScript source code and any Odata service definitions; this can include either JavaScript or node.js \(or both\) in sub-folders


The following example include modules for the following areas: database, Web, JavaScript application code, Odata \(optional\) services, and security \(OAuth2 client configuration\).



> ### Sample Code:  
> ```
> <myAppName>
> |- db/                        # Database deployment artifacts
> |  \- src/                    # Database artifacts: tables, views, etc.
> |- web/                       # Application router/descriptors
> |  \- resources/              # Static Web resources
> |- js/                        # JavaScript artifacts
> |  \- src/                    # JavaScript source code
> |     \- odata/               # OData resources (optional)
> |        \- srv/              # OData services
> \- security/                  # Security deployment artifacts/scopes/auths
> 
> ```

**Related Information**  


[Maintaining OData Services in SAP HANA Cloud](../050-HANA-Cloud-DB-Dev-Web-Access/maintaining-odata-services-in-sap-hana-cloud-78606fc.md "Define OData services for your Java and JavaScript multitarget applications in SAP HANA Cloud.")

[Working with the SAP Cloud Application Programming Model](working-with-the-sap-cloud-application-programming-model-166f4fb.md "Create a business application using the SAP Cloud Application Programming model.")

[The SAP Cloud Application Programming Model](https://cap.cloud.sap/docs)
