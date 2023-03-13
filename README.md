# CI-CD-Synapse-DP-with-integrated-AAD
YAML pipeline code for creating a DACPAC file from a Synapse dedicated pool with AAD integrated in Azure DevOps:

Note that you'll need to replace the placeholders <synapse-server-name>, <database-name>, <dacpac-file-name>, <azure-subscription> with your actual values.
Also, make sure to configure your Synapse dedicated pool to allow AAD integrated authentication before running the pipeline.

The azureSubscription variable in the pipeline code should be set to the name of the Azure subscription that contains the Synapse dedicated pool you want to connect to.
*******************************************************
This task is used to connect to the Synapse dedicated pool using AAD integrated authentication. It requires the following inputs:

azureSubscription: The name of the Azure subscription that contains the Synapse dedicated pool.
serverName: The name of the Synapse server that hosts the dedicated pool.
authenticationType: The authentication type to use when connecting to the dedicated pool. Set this to 'Azure Active Directory - Integrated' for AAD integrated authentication.
SqlPackage: This task is used to build the DACPAC file from the Synapse dedicated pool. It requires the following inputs:

action: The action to perform with SqlPackage. Set this to 'Export' to export the database schema to a DACPAC file.
sqlScript: The name of the database to export to the DACPAC file.
targetFile: The path and filename of the DACPAC file to create.
deployType: The type of deployment to use. Set this to 'None' to just build the DACPAC file.
additionalArguments: Any additional arguments to pass to SqlPackage. Set this to '/p:RegisterDataTierApplication=True' to register the DACPAC file as a data-tier application.
PublishBuildArtifacts: This task is used to publish the DACPAC file as a build artifact in Azure DevOps. It requires the following inputs:

artifactName: The name of the build artifact to create.
pathToPublish: The path to the DACPAC file to publish as the build artifact.
Make sure to configure the task inputs appropriately for your Synapse dedicated pool and pipeline requirements.
*******************************************************
