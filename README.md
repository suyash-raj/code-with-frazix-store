<a href="https://flotiq.com/">
    <img src="https://editor.flotiq.com/fonts/fq-logo.svg" alt="Flotiq logo" title="Flotiq" align="right" height="60" />
</a>  
  
Gatsby Starter: Ecommerce and Flotiq
========================


This is a [Gatsby](https://gatsbyjs.org) starter project for ecommerce using [Snipcart](https://snipcart.com). It's configured to pull products data from [Flotiq](https://flotiq.com) and can be easily deployed to your cloud hosting - Heroku, Netlify, Gatsby Cloud, etc.

Live Demo: https://flotiq-starter-products.herokuapp.com

Screenshot

<img src="https://github.com/flotiq/gatsby-starter-products/blob/master/docs/flotiq-starter-products.png" width=480 />

## Quick start

1. **Start the project from template using [Flotiq CLI]((https://github.com/flotiq/flotiq-cli))**

    ```bash
   npm install -g flotiq-cli
   flotiq start [flotiqApiKey] [projectName] https://github.com/flotiq/gatsby-starter-products.git
    ```
   * `flotiqApKey` - Read and write API key to your Flotiq account      
   * `projectName` - project name or project path (if you wish to start or import data from the current directory - use `.`)

1. **You can also start the project from template using Gatsby CLI**
    
    ```bash
    gatsby new gatsby-starter-products https://github.com/flotiq/gatsby-starter-products.git
    ```

1.  **Setup "Products" Content Type in Flotiq**

   Create your [Flotiq.com](https://editor.flotiq.com/register.html) account. 
   
   Next, create the `Product` Content Type:
   
   ![Create content type definition using Flotiq](docs/create-definition.png)
   
   _Note: You can also create `Product` using [Flotiq REST API](https://flotiq.com/docs/API/):_            
   
   ```sh
   curl 'https://api.flotiq.com/api/v1/internal/contenttype' -H 'X-AUTH-TOKEN: 1f69f8289d7cbd54a44d1d910ec31234' -H 'Content-Type: application/json;chars--data-binary ' -X POST --data-binary '{"name":"product","label":"Product","schemaDefinition":{"type":"object","allOf":[{"$ref":"#/components/schemas/AbstractContentTypeSchemaDefinition"},{"type":"object","properties":{"name":{"type":"string","minLength":1},"slug":{"type":"string","minLength":1},"price":{"type":"number","minLength":1},"description":{"type":"string"},"productImage":{"type":"array","items":{"$ref":"#/components/schemas/DataSource"},"minItems":0},"productGallery":{"type":"array","items":{"$ref":"#/components/schemas/DataSource"},"minItems":0}}}],"required":["name","slug","price"],"additionalProperties":false},"metaDefinition":{"propertiesConfig":{"name":{"label":"Name","inputType":"text","unique":true,"isTitlePart":true},"slug":{"label":"Slug","inputType":"text","unique":true},"price":{"label":"Price","inputType":"number","unique":false},"description":{"label":"Description","inputType":"richtext","unique":false},"productImage":{"label":"Product image","inputType":"datasource","unique":false,"validation":{"relationContenttype":"_media"}},"productGallery":{"label":"Product gallery","inputType":"datasource","unique":false,"validation":{"relationMultiple":true,"relationContenttype":"_media"}}},"order":["name","slug","price","description","productImage","productGallery"]}}'
   ```
  
1.  **Configure application**

   The last step is to configure our application to know from where it has to fetch the data.
   You can also setup your Snipcart API_KEY to enable store functionality. 
   
   You need to create a file called `.env` inside the root of the directory, with the following structure:

   ```
   GATSBY_FLOTIQ_API_KEY=YOUR FLOTIQ API KEY
   SNIPCART_API_KEY=YOUR SNIPCART PUBLIC API KEY
   ```

1.  **Start developing.**

    Navigate into your new site’s directory and start it up.
    
    ```sh
    cd gatsby-starter-products
    npm install
    gatsby develop
    ```
   
    This step is optional and is not necessary if you used flotiq-cli to start the project.
      
    If you wish to import example products to your account, before running `gatsby develop`, install [flotiq-cli](https://github.com/flotiq/flotiq-cli), and run in project directory:
      
    ```sh
    flotiq import [flotiqApiKey] .
    ```
    
    It will add 10 images and 4 products to your Flotiq account.
    
    _Note: You need to put your Read and write API key as the `flotiqApiKey` for import to work. You don't need the `Product` content type in your account. If you already have products with ids `product-1`, `product-2`, `product-3`, and `product-4` they will be overwritten._

1.  **Open the source code and start editing!**

    Your site is now running at `http://localhost:8000`!
    
    _Note: You'll also see a second link: _`http://localhost:8000/___graphql`_. This is a tool you can use to experiment with querying your data. Learn more about using this tool in the [Gatsby tutorial](https://www.gatsbyjs.org/tutorial/part-five/#introducing-graphiql)._
    
    Open a project directory in your code editor of choice and edit `src/pages/index.js`. Save your changes and the browser will update in real time!

1. **Manage your products using Flotiq editor**

    You can easily manage your products using Flotiq editor
    
    ![](docs/manage-products.png)
 

## Deploy

  You can deploy this project to Heroku in 3 minutes:

  [![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/flotiq/gatsby-starter-products)

  Or to Netlify:

  [![Deploy](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/flotiq/gatsby-starter-products)


## Collaborating

   If you wish to talk with us about this project, feel free to hop on our [![Discord Chat](https://img.shields.io/discord/682699728454025410.svg)](https://discord.gg/FwXcHnX).
   
   If you found a bug, please report it in [issues](https://github.com/flotiq/gatsby-starter-products/issues).
