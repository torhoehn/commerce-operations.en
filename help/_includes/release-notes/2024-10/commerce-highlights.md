# October 2024 Adobe Commerce 2.4.7-beta highlights

## Highlights

This release of Adobe Commerce includes several critical security fixes and platform improvements.

### Security

The following security enhancements in this release improve compiance with the latest security best practices:

>[!NOTE]
>
>For the latest information about the security bug fixes, see [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Settings</strong></td>
            <td>This release includes the following enhancements to security settings:
              <ul>
                <li><strong>Encryption key rotation</strong>: A new CLI command is now available for changing your encryption key. See the <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Troubleshooting Encryption Key Rotation: CVE-2024-34102</a> Knowledge Base article for details.<!-- AC-12589 --></li>
                <li><strong>One-time password (OTP) settings</strong>: This update is required to resolve an error that was introduced by a <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">backward-incompatible change</a> in 2.4.7. The description of the <strong>[!UICONTROL OTP Window]</strong> field now provides an accurate explanation of the setting and the default value has been changed from <code>1</code> to <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Platform

The following platform upgrades for this release ensure that Adobe Commerce remains a robust and reliable platform, ready to meet the demands of modern commerce environments:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Database</strong></td>
            <td>In alignment with our <a href="/help/release/lifecycle-policy.md">support lifecycle policy</a>, Adobe Commerce is now compatible with the following long-term support (LTS) versions of the following database technologies:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(supported until 2029)_</em>: The previous version (MariaDB 10.6) reaches end-of-life in 2026, making this upgrade essential for maintaining system integrity and performance. MariaDB 10.6 is still supported, but Adobe recommends upgrading to MariaDB 11.4 when upgrading to Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(supported until 2032)_</em>: The previous version (MySQL 8.0) reaches end-of-life in 2026, making this upgrade essential for maintaining system integrity and performance. MySQL 8.0 is still supported, but Adobe recommends upgrading to MySQL 8.4 when upgrading to Adobe Commerce 2.4.8</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>This release includes the following PHP enhancements:
            <ul>
              <li><strong>PHP 8.1</strong>: This release removes PHP 8.1 compatibilty for Adobe Commerce 2.4.8. You must upgrade to PHP 8.3 before upgrading to Adobe Commerce 2.4.8.</li>
              <li><strong>PHP 8.2</strong>: One of the significant changes in PHP 8.2 involves the deprecation of passing null to non-nullable internal function parameters. This release addresses deprecated PHP 8.1 features in core platform components and ensures compatibility with PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong>: This release addresses several critical issues, enhances compatibility, and ensures that the Adobe Commerce testing framework aligns with the latest industry standards. Adobe recommends that all Commerce Marketplace vendors and customers with customizations verify that their unit and integration tests run on PHPUnit 10 instead of 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Components</strong></td>
            <td>The following third-party <a href="/help/release/packages/adobe-commerce.md">components and dependencies</a> were updated to the latest stable versions to enhance platform stability and performance:
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Search</strong></td>
            <td>Adobe Commerce is now optimized for OpenSearch 2.x and is no longer compatible with Elasticsearch. All Elasticsearch 7 and 8 modules and classes are now deprecated in the codebase. Adobe strongly recommends transitioning to OpenSearch for both on-premises and cloud infrastructure deployments to ensure continued support and compatibility. See <a href="/help/upgrade/prepare/opensearch-migration.md">Migrating to OpenSearch</a>.
              <ul>
                <li>The Elasticsearch 7 and Elasticsearch 8 options are now labeled as "(Deprecated)" in the Admin configuration.</li>
                <li>When a user selects Elasticsearch as the search engine in the Admin configuration, Commerce displays a notification stating, <em>"This search engine option is no longer supported by Adobe. We recommend using OpenSearch as a search engine instead."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Performance

This release includes the following performance enhancements:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Indexers</strong></td>
            <td>The default <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">indexer mode</a> for all indexers is now [!UICONTROL **Update by Schedule**] when installing a new version of Adobe Commerce or upgrading from a previous version. The new default ensures that indexers are in the recommended configuration, improving system performance and reducing potential issues.</td>
        </tr>
    </tbody>
</table>

### Quality

This release includes the following quality enhancements:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Inventory</strong></td>
           <td>The system now operates without the previously hidden dependency from Catalog introduced by InventoryIndexer, ensuring that the product creation, display mode switch, stock status change, and other related functionalities work as expected. Previously, this hidden dependency caused inconsistencies as different entities were synchronized and the indexer used different entities.</td>
        </tr>
        <tr>
            <td><strong>Orders</strong></td>
            <td>To minimize confusion, the [!UICONTROL **Submit Comment**] button label changed to [!UICONTROL **Update**] in the <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">order detail</a> page.</td>
        </tr>
    </tbody>
</table>

### GraphQL

This release includes the following GraphQL enhancements:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>General enhancements</strong></td>
           <td>This release includes the following general GraphQL API enhancements:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: Added the <code>grouped_product_image</code> and <code>configurable_product_image</code> fields to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a> type.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: Added the following new fields to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> type to support accurate pricing display and discount calculations:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>: Added the <code>grand_total_excluding_tax</code> field to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a> type, providing clear tax-inclusive pricing.</li>
              <li><!--LYNX-542--><strong>updateCartItems mutation</strong>: Updated the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> mutation to return success responses with error details instead of exceptions. Enhanced error mapping to improve the clarity of user notifications.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config query</strong>: Introduced a <code>theme</code> field to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a> query. This field allows you to specify the name of the theme to use to render the reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: Introduced a <code>quantity</code> field in the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> to provide stock level details. It displays available stock or null based on Admin settings.</li>
               <li><!--LYNX-460--><strong>Bundle products</strong>: Corrected pricing display for bundle products, ensuring accurate price and currency information.</li>
               <li><!--LYNX-547--><strong>Quantity</strong>: Refined messaging for insufficient and unavailable quantity notifications.</li>
               <li><!--LYNX-541--><strong>InsufficientStockError type</strong>: Added a new <code>InsufficientStockError</code> type to handle cases where stock levels are insufficient. Adjusted the schema to support new error types, enhancing error reporting capabilities.</li>
               <li><!--LYNX-476--><strong>Inventory amount</strong>: Enhanced error messaging to include available inventory amounts. Provides users with clearer insights into stock levels during order updates.</li>
               <li><!--LYNX-377--><strong>Requested quantity</strong>: Added the <code>not_available_message</code> to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Customer management</strong></td>
           <td>This release includes the following customer management enhancements:
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken mutation</strong>: Refined error handling in the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> mutation to provide specific messages for unconfirmed emails. Supports better user guidance and error resolution.</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail mutation</strong>: Added a new <code>resendConfirmationEmail</code> mutation for resending email confirmations.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Order management</strong></td>
           <td>This release includes the following user order management enhancements:
             <ul>
              <li><!--LYNX-470--><strong>Date of first order</strong>: Added a new <code>date_of_first_order</code> field to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a> type.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: Extended the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> type to include custom attributes, enhancing order detail visibility. Supports additional information display on order confirmation pages.</li>
              <li><!--LYNX-458--><strong>guestOrder and guestOrderByToken queries</strong>: Updated the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> and <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> queries to include custom address attributes, ensuring complete address information for new accounts.</li>
              <li><!--LYNX-450--><strong>CustomerOrder type</strong>: Added the<code>is_virtual</code> field to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> type, supporting virtual product identification. Enhances order processing by distinguishing virtual from physical products.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: Added an <code>OrderItemPrices</code> type similar to <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> to <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> with several new fields for price.</li>
              <li><!--LYNX-448--><strong>Merge guest orders</strong>: Improved API functionality to merge guest orders with customer accounts based on email matching. Streamlines order management for returning customers.</li>
              <li><!-- LYNX-523: --><strong>available_actions field</strong>: Extended the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> type to include an <code>available_actions</code> field for better order management. The `available_actions` field maps to an enumeration that lists the possible actions that can be performed on the order.</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder type</strong>: Added the <code>customer_info</code> field to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> type. This field requires and <code>OrderCustomerInfo</code>, which defines details about the customer name.</li>
              <li><!--LYNX-519--><strong>Error codes for order cancellation</strong>: Added detailed error codes to the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a> type. Improved error handling and user feedback for the order cancellation processes.</li>
              <li><!--LYNX-515--><strong>Enabled guest users to create returns for orders</strong>: Adjusted the <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> mutation to support guest order returns.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong>: Added a new <code>confirmCancelOrder</code> mutation to facilitate order cancellation for guest users.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
