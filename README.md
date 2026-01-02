<!doctype html>
<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MW Management System</title>
  <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        /* Header Styles */
        .header {
            background: white;
            padding: 20px 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .header h1 {
            color: #667eea;
            font-size: 28px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .user-info span {
            color: #333;
            font-weight: 500;
        }

        .btn-logout {
            background: #dc3545;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }

        .btn-logout:hover {
            background: #c82333;
        }

        /* Auth Section Styles */
        .auth-section {
            max-width: 450px;
            margin: 100px auto;
            background: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .auth-section h2 {
            color: #667eea;
            margin-bottom: 30px;
            text-align: center;
            font-size: 32px;
        }

        .auth-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
        }

        .auth-tab {
            flex: 1;
            padding: 12px;
            border: none;
            background: #f0f0f0;
            color: #666;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
            transition: all 0.3s;
        }

        .auth-tab.active {
            background: #667eea;
            color: white;
        }

        .auth-form {
            display: none;
        }

        .auth-form.active {
            display: block;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #333;
            font-weight: 500;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 5px;
            font-size: 14px;
            transition: border-color 0.3s;
        }

        .form-group input:focus {
            outline: none;
            border-color: #667eea;
        }

        .btn-primary {
            width: 100%;
            padding: 14px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
        }

        .btn-primary:hover {
            background: #5568d3;
        }

        .btn-primary:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        /* Main App Styles */
        .main-app {
            display: none;
        }

        .controls {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }

        .controls-row {
            display: flex;
            gap: 20px;
            align-items: flex-end;
            flex-wrap: wrap;
        }

        .control-group {
            flex: 0 0 250px;
            min-width: 200px;
        }

        .control-group label {
            display: block;
            margin-bottom: 8px;
            color: #333;
            font-weight: 500;
        }

        .control-group select,
        .control-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 5px;
            font-size: 14px;
        }

        .btn-secondary {
            padding: 12px 30px;
            background: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: background 0.3s;
        }

        .btn-secondary:hover {
            background: #218838;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            background: white;
            padding: 20px 20px 0 20px;
            border-radius: 10px 10px 0 0;
        }

        .tab {
            padding: 12px 30px;
            background: #f0f0f0;
            border: none;
            cursor: pointer;
            border-radius: 5px 5px 0 0;
            font-size: 16px;
            font-weight: 500;
            transition: all 0.3s;
        }

        .tab.active {
            background: #667eea;
            color: white;
        }

        /* Table Styles */
        .table-container {
            background: white;
            border-radius: 0 0 10px 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .table-wrapper {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            min-width: 1200px;
        }

        thead {
            background: #667eea;
            color: white;
        }

        th {
            padding: 15px;
            text-align: left;
            font-weight: 600;
            font-size: 14px;
        }

        td {
            padding: 12px 15px;
            border-bottom: 1px solid #e0e0e0;
            font-size: 14px;
        }

        tbody tr:hover {
            background: #f8f9fa;
        }

        .badge {
            padding: 4px 12px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 600;
        }

        .badge-yes {
            background: #d4edda;
            color: #155724;
        }

        .badge-no {
            background: #f8d7da;
            color: #721c24;
        }

        .badge-lv {
            background: #cce5ff;
            color: #004085;
        }

        .badge-dl {
            background: #d1ecf1;
            color: #0c5460;
        }

        .actions {
            display: flex;
            gap: 8px;
        }

        .btn-icon {
            padding: 6px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s;
        }

        .btn-edit {
            background: #ffc107;
            color: #000;
        }

        .btn-edit:hover {
            background: #e0a800;
        }

        .btn-delete {
            background: #dc3545;
            color: white;
        }

        .btn-delete:hover {
            background: #c82333;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            z-index: 1000;
            overflow-y: auto;
            backdrop-filter: blur(3px);
        }

        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .modal-content {
            background: white;
            padding: 0;
            border-radius: 15px;
            max-width: 900px;
            width: 100%;
            max-height: 90vh;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            animation: modalSlideIn 0.3s ease-out;
        }

        @keyframes modalSlideIn {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 30px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .modal-header h3 {
            color: white;
            font-size: 24px;
            margin: 0;
        }

        .btn-close {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: white;
            padding: 0;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .btn-close:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: rotate(90deg);
        }

        .modal-body {
            padding: 30px;
            max-height: calc(90vh - 150px);
            overflow-y: auto;
        }

        .modal-section {
            margin-bottom: 30px;
        }

        .modal-section:last-child {
            margin-bottom: 0;
        }

        .modal-section-title {
            font-size: 16px;
            font-weight: 600;
            color: #667eea;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e0e0e0;
        }

        .modal-form {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
        }

        .modal-form .form-group {
            display: flex;
            flex-direction: column;
        }

        .modal-form .form-group.full-width {
            grid-column: 1 / -1;
        }

        .modal-form .form-group label {
            font-size: 13px;
            font-weight: 600;
            color: #555;
            margin-bottom: 8px;
        }

        .modal-form .form-group label .required {
            color: #dc3545;
            margin-left: 3px;
        }

        .modal-form .form-group input,
        .modal-form .form-group select {
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 14px;
            transition: all 0.3s;
        }

        .modal-form .form-group input:focus,
        .modal-form .form-group select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .modal-actions {
            display: flex;
            gap: 10px;
            justify-content: flex-end;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 2px solid #e0e0e0;
        }

        .btn-cancel {
            padding: 12px 30px;
            background: #6c757d;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
        }

        .btn-cancel:hover {
            background: #5a6268;
        }

        /* Message Styles */
        .message {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 5px;
            color: white;
            font-weight: 500;
            z-index: 2000;
            animation: slideIn 0.3s ease-out;
            max-width: 400px;
        }

        .message.success {
            background: #28a745;
        }

        .message.error {
            background: #dc3545;
        }

        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        /* Loading Spinner */
        .loading {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 2000;
        }

        .loading.active {
            display: block;
        }

        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: #999;
        }

        .empty-state h3 {
            font-size: 20px;
            margin-bottom: 10px;
        }

        .empty-state p {
            font-size: 14px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 15px;
            }

            .controls-row {
                flex-direction: column;
            }

            .modal-form {
                grid-template-columns: 1fr;
            }

            .tabs {
                overflow-x: auto;
            }
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div class="container"><!-- Authentication Section -->
   <div id="authSection" class="auth-section">
    <h2>MW Management System</h2>
    <div class="auth-tabs"><button class="auth-tab active" onclick="switchAuthTab('login')">Login</button> <button class="auth-tab" onclick="switchAuthTab('register')">Register</button>
    </div><!-- Download Button -->
    <div style="text-align: center; margin-bottom: 20px;"><button class="btn-secondary" onclick="downloadProjectFiles()" style="background: #17a2b8; width: 100%;"> 📥 Download Complete API Project Files </button>
    </div><!-- Login Form -->
    <form id="loginForm" class="auth-form active" onsubmit="login(event)">
     <div class="form-group"><label for="loginUsername">Username</label> <input type="text" id="loginUsername" required>
     </div>
     <div class="form-group"><label for="loginPassword">Password</label> <input type="password" id="loginPassword" required>
     </div><button type="submit" class="btn-primary">Login</button>
    </form><!-- Register Form -->
    <form id="registerForm" class="auth-form" onsubmit="register(event)">
     <div class="form-group"><label for="registerUsername">Username</label> <input type="text" id="registerUsername" required minlength="3">
     </div>
     <div class="form-group"><label for="registerEmail">Email</label> <input type="email" id="registerEmail" required>
     </div>
     <div class="form-group"><label for="registerFullName">Full Name</label> <input type="text" id="registerFullName" required>
     </div>
     <div class="form-group"><label for="registerPassword">Password</label> <input type="password" id="registerPassword" required minlength="6">
     </div><button type="submit" class="btn-primary">Register</button>
    </form>
   </div><!-- Main Application -->
   <div id="mainApp" class="main-app"><!-- Header -->
    <div class="header">
     <h1>MW Management System</h1>
     <div class="user-info"><span>Welcome, <strong id="userFullName"></strong></span> <button class="btn-logout" onclick="logout()">Logout</button>
     </div>
    </div><!-- Controls -->
    <div class="controls">
     <div class="controls-row">
      <div class="control-group"><label for="monthSelect">Select Month</label> <select id="monthSelect" onchange="loadRecords()"> <option value="">Select Month</option> </select>
      </div><button class="btn-secondary" onclick="openAddModal()">+ Add New Record</button> <button class="btn-secondary" onclick="exportToCSV()" style="background: #28a745;">📊 Export to CSV</button> <button class="btn-secondary" onclick="downloadProjectFiles()" style="background: #17a2b8;">📥 Download API Project</button>
     </div>
    </div><!-- Tabs -->
    <div class="tabs"><button class="tab active" onclick="switchTab('cleanup')">Cleanup Records</button> <button class="tab" onclick="switchTab('deployment')">Deployment Records</button>
    </div><!-- Tables -->
    <div id="cleanupTable" class="table-container">
     <div class="table-wrapper">
      <table>
       <thead>
        <tr>
         <th>Application Name</th>
         <th>Assigned</th>
         <th>Go</th>
         <th>CCR Checked</th>
         <th>Bin2Prod</th>
         <th>Config2Prod</th>
         <th>RD Checked</th>
         <th>CF Checked</th>
         <th>CCR Number</th>
         <th>Jira</th>
         <th>Actions</th>
        </tr>
       </thead>
       <tbody id="cleanupTableBody"><!-- Data will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
    <div id="deploymentTable" class="table-container" style="display: none;">
     <div class="table-wrapper">
      <table>
       <thead>
        <tr>
         <th>Application Name</th>
         <th>Validated</th>
         <th>Assigned To</th>
         <th>Environment</th>
         <th>Release Created</th>
         <th>Release Checked</th>
         <th>Deployed</th>
         <th>Release URL</th>
         <th>Actions</th>
        </tr>
       </thead>
       <tbody id="deploymentTableBody"><!-- Data will be populated here -->
       </tbody>
      </table>
     </div>
    </div>
   </div>
  </div><!-- Cleanup Modal -->
  <div id="cleanupModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3 id="cleanupModalTitle">Add Cleanup Record</h3><button class="btn-close" onclick="closeModal('cleanupModal')">×</button>
    </div>
    <div class="modal-body">
     <form id="cleanupForm" onsubmit="saveCleanupRecord(event)"><input type="hidden" id="cleanupRecordId"> <!-- Basic Information -->
      <div class="modal-section">
       <div class="modal-section-title">
        ��� Basic Information
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="cleanupMWMonth">MW Month<span class="required">*</span></label> <input type="text" id="cleanupMWMonth" required>
        </div>
        <div class="form-group"><label for="cleanupApplicationName">Application Name<span class="required">*</span></label> <input type="text" id="cleanupApplicationName" required>
        </div>
        <div class="form-group"><label for="cleanupAssigned">Assigned To<span class="required">*</span></label> <input type="text" id="cleanupAssigned" required>
        </div>
        <div class="form-group"><label for="cleanupGo">Go Status<span class="required">*</span></label> <select id="cleanupGo" required> <option value="">Select Status</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group full-width"><label for="cleanupIfNoWhy">If No, Why?</label> <input type="text" id="cleanupIfNoWhy" placeholder="Reason for No status">
        </div>
       </div>
      </div><!-- Validation Status -->
      <div class="modal-section">
       <div class="modal-section-title">
        ✅ Validation Status
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="cleanupCCRChecked">CCR Checked<span class="required">*</span></label> <select id="cleanupCCRChecked" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="cleanupBin2Prod">Bin2Prod<span class="required">*</span></label> <select id="cleanupBin2Prod" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="cleanupConfig2Prod">Config2Prod<span class="required">*</span></label> <select id="cleanupConfig2Prod" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="cleanupRDChecked">RD Checked<span class="required">*</span></label> <select id="cleanupRDChecked" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="cleanupCFChecked">CF Checked<span class="required">*</span></label> <select id="cleanupCFChecked" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="cleanupCheckedDate">Checked Date<span class="required">*</span></label> <input type="date" id="cleanupCheckedDate" required>
        </div>
       </div>
      </div><!-- Documentation -->
      <div class="modal-section">
       <div class="modal-section-title">
        📄 Documentation &amp; References
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="cleanupCCRNumber">CCR Number</label> <input type="text" id="cleanupCCRNumber" placeholder="CCR-XXXX">
        </div>
        <div class="form-group"><label for="cleanupJira">Jira Ticket</label> <input type="text" id="cleanupJira" placeholder="PROJ-XXXX">
        </div>
        <div class="form-group full-width"><label for="cleanupRepository">Repository</label> <input type="text" id="cleanupRepository" placeholder="Repository URL or name">
        </div>
        <div class="form-group full-width"><label for="cleanupLASCODE02Path">LASCODE02 Path</label> <input type="text" id="cleanupLASCODE02Path" placeholder="Path to LASCODE02">
        </div>
       </div>
      </div><!-- Deployment Status -->
      <div class="modal-section">
       <div class="modal-section-title">
        🚀 Deployment Status
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="cleanupMovedToDoNotDeploy">Moved To DoNotDeploy<span class="required">*</span></label> <select id="cleanupMovedToDoNotDeploy" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group full-width"><label for="cleanupCommentsNotes">Comments/Notes</label> <input type="text" id="cleanupCommentsNotes" placeholder="Additional comments or notes">
        </div>
       </div>
      </div>
      <div class="modal-actions"><button type="button" class="btn-cancel" onclick="closeModal('cleanupModal')">Cancel</button> <button type="submit" class="btn-primary">Save Record</button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Deployment Modal -->
  <div id="deploymentModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3 id="deploymentModalTitle">Add Deployment Record</h3><button class="btn-close" onclick="closeModal('deploymentModal')">×</button>
    </div>
    <div class="modal-body">
     <form id="deploymentForm" onsubmit="saveDeploymentRecord(event)"><input type="hidden" id="deploymentRecordId"> <!-- Basic Information -->
      <div class="modal-section">
       <div class="modal-section-title">
        📋 Basic Information
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="deploymentMWMonth">MW Month<span class="required">*</span></label> <input type="text" id="deploymentMWMonth" required>
        </div>
        <div class="form-group"><label for="deploymentApplicationName">Application Name<span class="required">*</span></label> <input type="text" id="deploymentApplicationName" required>
        </div>
        <div class="form-group"><label for="deploymentValidated">Validated<span class="required">*</span></label> <select id="deploymentValidated" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="deploymentAssignedTo">Assigned To<span class="required">*</span></label> <input type="text" id="deploymentAssignedTo" required>
        </div>
        <div class="form-group"><label for="deploymentEnvironment">Environment<span class="required">*</span></label> <select id="deploymentEnvironment" required> <option value="">Select Environment</option> <option value="LV">LV</option> <option value="DL">DL</option> </select>
        </div>
       </div>
      </div><!-- Release Information -->
      <div class="modal-section">
       <div class="modal-section-title">
        🚀 Release Information
       </div>
       <div class="modal-form">
        <div class="form-group"><label for="deploymentReleaseCreated">Release Created<span class="required">*</span></label> <select id="deploymentReleaseCreated" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="deploymentReleaseChecked">Release Checked<span class="required">*</span></label> <select id="deploymentReleaseChecked" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group"><label for="deploymentDeployed">Deployed<span class="required">*</span></label> <select id="deploymentDeployed" required> <option value="">Select</option> <option value="Yes">Yes</option> <option value="No">No</option> </select>
        </div>
        <div class="form-group full-width"><label for="deploymentReleaseURL">Release URL</label> <input type="text" id="deploymentReleaseURL" placeholder="https://">
        </div>
       </div>
      </div><!-- Additional Notes -->
      <div class="modal-section">
       <div class="modal-section-title">
        📝 Additional Information
       </div>
       <div class="modal-form">
        <div class="form-group full-width"><label for="deploymentCommentsNotes">Comments/Notes</label> <input type="text" id="deploymentCommentsNotes" placeholder="Additional comments or notes">
        </div>
       </div>
      </div>
      <div class="modal-actions"><button type="button" class="btn-cancel" onclick="closeModal('deploymentModal')">Cancel</button> <button type="submit" class="btn-primary">Save Record</button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Loading Spinner -->
  <div id="loading" class="loading">
   <div class="spinner"></div>
  </div>
  <script>
        // ===================================
        // Configuration
        // ===================================
        const API_BASE_URL = 'https://localhost:7204/api';

        // ===================================
        // Global State
        // ===================================
        let currentTab = 'cleanup';
        let cleanupRecords = [];
        let deploymentRecords = [];
        let editingRecordId = null;

        // ===================================
        // Initialization
        // ===================================
        document.addEventListener('DOMContentLoaded', function() {
            initializeMonthDropdown();
            
            if (checkAuth()) {
                showMainApp();
            } else {
                showAuthSection();
            }
        });

        function initializeMonthDropdown() {
            const monthSelect = document.getElementById('monthSelect');
            const months = [
                'January', 'February', 'March', 'April', 'May', 'June',
                'July', 'August', 'September', 'October', 'November', 'December'
            ];
            
            const currentDate = new Date();
            const currentYear = currentDate.getFullYear();
            const nextYear = currentYear + 1;
            
            // Generate months for current and next year
            const options = [];
            [currentYear, nextYear].forEach(year => {
                months.forEach(month => {
                    options.push(`${month} ${year}`);
                });
            });
            
            options.forEach(option => {
                const optionElement = document.createElement('option');
                optionElement.value = option;
                optionElement.textContent = option;
                monthSelect.appendChild(optionElement);
            });
            
            // Set default to current month
            const currentMonth = months[currentDate.getMonth()];
            monthSelect.value = `${currentMonth} ${currentYear}`;
        }

        // ===================================
        // Authentication Functions
        // ===================================
        function switchAuthTab(tab) {
            const tabs = document.querySelectorAll('.auth-tab');
            const forms = document.querySelectorAll('.auth-form');
            
            tabs.forEach(t => t.classList.remove('active'));
            forms.forEach(f => f.classList.remove('active'));
            
            if (tab === 'login') {
                tabs[0].classList.add('active');
                document.getElementById('loginForm').classList.add('active');
            } else {
                tabs[1].classList.add('active');
                document.getElementById('registerForm').classList.add('active');
            }
        }

        async function register(event) {
            event.preventDefault();
            
            const username = document.getElementById('registerUsername').value.trim();
            const email = document.getElementById('registerEmail').value.trim();
            const fullName = document.getElementById('registerFullName').value.trim();
            const password = document.getElementById('registerPassword').value;
            
            if (!username || !email || !fullName || !password) {
                showMessage('Please fill in all fields', 'error');
                return;
            }
            
            try {
                showLoading(true);
                
                const response = await fetch(`${API_BASE_URL}/auth/register`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({
                        username,
                        email,
                        fullName,
                        password
                    })
                });
                
                const data = await response.json();
                
                if (!response.ok) {
                    throw new Error(data.error || data.title || 'Registration failed');
                }
                
                showMessage('Registration successful! Please login.', 'success');
                switchAuthTab('login');
                document.getElementById('registerForm').reset();
                
            } catch (error) {
                console.error('Registration error:', error);
                showMessage(error.message || 'Registration failed. Please try again.', 'error');
            } finally {
                showLoading(false);
            }
        }

        async function login(event) {
            event.preventDefault();
            
            const username = document.getElementById('loginUsername').value.trim();
            const password = document.getElementById('loginPassword').value;
            
            if (!username || !password) {
                showMessage('Please enter username and password', 'error');
                return;
            }
            
            try {
                showLoading(true);
                
                const response = await fetch(`${API_BASE_URL}/auth/login`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({ username, password })
                });
                
                const data = await response.json();
                
                if (!response.ok) {
                    throw new Error(data.error || data.title || 'Login failed');
                }
                
                // Store authentication data
                localStorage.setItem('token', data.token);
                localStorage.setItem('username', data.username);
                localStorage.setItem('fullName', data.fullName);
                localStorage.setItem('userId', data.userId.toString());
                localStorage.setItem('tokenExpiry', data.expiresAt);
                
                showMessage('Login successful!', 'success');
                showMainApp();
                
            } catch (error) {
                console.error('Login error:', error);
                showMessage(error.message || 'Login failed. Please try again.', 'error');
            } finally {
                showLoading(false);
            }
        }

        function checkAuth() {
            const token = localStorage.getItem('token');
            const tokenExpiry = localStorage.getItem('tokenExpiry');
            
            if (!token) {
                return false;
            }
            
            // Check if token is expired
            if (tokenExpiry) {
                const expiryDate = new Date(tokenExpiry);
                const now = new Date();
                
                if (now >= expiryDate) {
                    logout();
                    return false;
                }
            }
            
            return true;
        }

        function logout() {
            localStorage.clear();
            showAuthSection();
            document.getElementById('loginForm').reset();
            showMessage('Logged out successfully', 'success');
        }

        function showMainApp() {
            document.getElementById('authSection').style.display = 'none';
            document.getElementById('mainApp').style.display = 'block';
            document.getElementById('userFullName').textContent = localStorage.getItem('fullName') || 'User';
            loadRecords();
        }

        function showAuthSection() {
            document.getElementById('mainApp').style.display = 'none';
            document.getElementById('authSection').style.display = 'block';
        }

        // ===================================
        // API Helper Functions
        // ===================================
        async function fetchWithAuth(url, options = {}) {
            const token = localStorage.getItem('token');
            
            if (!token) {
                throw new Error('No authentication token found');
            }
            
            const headers = {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${token}`,
                ...options.headers
            };
            
            const response = await fetch(url, { ...options, headers });
            
            if (response.status === 401) {
                logout();
                throw new Error('Session expired. Please login again.');
            }
            
            return response;
        }

        // ===================================
        // Tab Switching
        // ===================================
        function switchTab(tab) {
            currentTab = tab;
            
            const tabs = document.querySelectorAll('.tab');
            tabs.forEach(t => t.classList.remove('active'));
            
            if (tab === 'cleanup') {
                tabs[0].classList.add('active');
                document.getElementById('cleanupTable').style.display = 'block';
                document.getElementById('deploymentTable').style.display = 'none';
            } else {
                tabs[1].classList.add('active');
                document.getElementById('cleanupTable').style.display = 'none';
                document.getElementById('deploymentTable').style.display = 'block';
            }
        }

        // ===================================
        // Load Records
        // ===================================
        async function loadRecords() {
            const month = document.getElementById('monthSelect').value;
            
            if (!month) {
                showMessage('Please select a month', 'error');
                return;
            }
            
            await Promise.all([
                loadCleanupRecords(month),
                loadDeploymentRecords(month)
            ]);
        }

        async function loadCleanupRecords(month = null) {
            if (!month) {
                month = document.getElementById('monthSelect').value;
            }
            
            if (!month) return;
            
            try {
                showLoading(true);
                
                const response = await fetchWithAuth(`${API_BASE_URL}/cleanup?mwMonth=${encodeURIComponent(month)}`);
                
                if (!response.ok) {
                    throw new Error('Failed to load cleanup records');
                }
                
                cleanupRecords = await response.json();
                renderCleanupTable();
                
            } catch (error) {
                console.error('Error loading cleanup records:', error);
                showMessage(error.message || 'Failed to load cleanup records', 'error');
            } finally {
                showLoading(false);
            }
        }

        async function loadDeploymentRecords(month = null) {
            if (!month) {
                month = document.getElementById('monthSelect').value;
            }
            
            if (!month) return;
            
            try {
                showLoading(true);
                
                const response = await fetchWithAuth(`${API_BASE_URL}/deployment?mwMonth=${encodeURIComponent(month)}`);
                
                if (!response.ok) {
                    throw new Error('Failed to load deployment records');
                }
                
                deploymentRecords = await response.json();
                renderDeploymentTable();
                
            } catch (error) {
                console.error('Error loading deployment records:', error);
                showMessage(error.message || 'Failed to load deployment records', 'error');
            } finally {
                showLoading(false);
            }
        }

        // ===================================
        // Render Tables
        // ===================================
        function renderCleanupTable() {
            const tbody = document.getElementById('cleanupTableBody');
            
            if (cleanupRecords.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="11" class="empty-state">
                            <h3>No Records Found</h3>
                            <p>No cleanup records for the selected month</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            tbody.innerHTML = cleanupRecords.map(record => {
                // Safe helper function to handle null/undefined values for badges
                const safeBadge = (value) => {
                    if (!value) return '<span class="badge badge-no">-</span>';
                    const lower = value.toLowerCase();
                    return `<span class="badge badge-${lower}">${value}</span>`;
                };
                
                // Safe helper function to handle null/undefined values for text
                const safeText = (value) => value || '-';
                
                return `
                    <tr>
                        <td>${escapeHtml(safeText(record.applicationName))}</td>
                        <td>${escapeHtml(safeText(record.assigned))}</td>
                        <td>${safeBadge(record.go)}</td>
                        <td>${safeBadge(record.ccrChecked)}</td>
                        <td>${safeBadge(record.bin2Prod)}</td>
                        <td>${safeBadge(record.config2Prod)}</td>
                        <td>${safeBadge(record.rdChecked)}</td>
                        <td>${safeBadge(record.cfChecked)}</td>
                        <td>${escapeHtml(safeText(record.ccrNumber))}</td>
                        <td>${escapeHtml(safeText(record.jira))}</td>
                        <td class="actions">
                            <button class="btn-icon btn-edit" onclick="editCleanupRecord(${record.cleanupRecordId})">Edit</button>
                            <button class="btn-icon btn-delete" onclick="deleteCleanupRecord(${record.cleanupRecordId})">Delete</button>
                        </td>
                    </tr>
                `;
            }).join('');
        }

        function renderDeploymentTable() {
            const tbody = document.getElementById('deploymentTableBody');
            
            if (deploymentRecords.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="9" class="empty-state">
                            <h3>No Records Found</h3>
                            <p>No deployment records for the selected month</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            tbody.innerHTML = deploymentRecords.map(record => {
                // Safe helper function to handle null/undefined values for badges
                const safeBadge = (value) => {
                    if (!value) return '<span class="badge badge-no">-</span>';
                    const lower = value.toLowerCase();
                    return `<span class="badge badge-${lower}">${value}</span>`;
                };
                
                // Safe helper function to handle null/undefined values for text
                const safeText = (value) => value || '-';
                
                return `
                    <tr>
                        <td>${escapeHtml(safeText(record.applicationName))}</td>
                        <td>${safeBadge(record.validated)}</td>
                        <td>${escapeHtml(safeText(record.assignedTo))}</td>
                        <td>${safeBadge(record.environment)}</td>
                        <td>${safeBadge(record.releaseCreated)}</td>
                        <td>${safeBadge(record.releaseChecked)}</td>
                        <td>${safeBadge(record.deployed)}</td>
                        <td><a href="${escapeHtml(safeText(record.releaseURL))}" target="_blank" rel="noopener noreferrer">View</a></td>
                        <td class="actions">
                            <button class="btn-icon btn-edit" onclick="editDeploymentRecord(${record.deploymentRecordId})">Edit</button>
                            <button class="btn-icon btn-delete" onclick="deleteDeploymentRecord(${record.deploymentRecordId})">Delete</button>
                        </td>
                    </tr>
                `;
            }).join('');
        }

        // ===================================
        // Modal Functions
        // ===================================
        function openAddModal() {
            editingRecordId = null;
            
            if (currentTab === 'cleanup') {
                document.getElementById('cleanupModalTitle').textContent = 'Add Cleanup Record';
                document.getElementById('cleanupForm').reset();
                document.getElementById('cleanupRecordId').value = '';
                document.getElementById('cleanupMWMonth').value = document.getElementById('monthSelect').value;
                openModal('cleanupModal');
            } else {
                document.getElementById('deploymentModalTitle').textContent = 'Add Deployment Record';
                document.getElementById('deploymentForm').reset();
                document.getElementById('deploymentRecordId').value = '';
                document.getElementById('deploymentMWMonth').value = document.getElementById('monthSelect').value;
                openModal('deploymentModal');
            }
        }

        function openModal(modalId) {
            document.getElementById(modalId).classList.add('active');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        // ===================================
        // Cleanup Record Functions
        // ===================================
        function editCleanupRecord(id) {
            const record = cleanupRecords.find(r => r.cleanupRecordId === id);
            if (!record) return;
            
            editingRecordId = id;
            document.getElementById('cleanupModalTitle').textContent = 'Edit Cleanup Record';
            document.getElementById('cleanupRecordId').value = id;
            document.getElementById('cleanupMWMonth').value = record.mwMonth;
            document.getElementById('cleanupApplicationName').value = record.applicationName;
            document.getElementById('cleanupAssigned').value = record.assigned;
            document.getElementById('cleanupGo').value = record.go;
            document.getElementById('cleanupIfNoWhy').value = record.ifNoWhy || '';
            document.getElementById('cleanupCCRChecked').value = record.ccrChecked;
            document.getElementById('cleanupBin2Prod').value = record.bin2Prod;
            document.getElementById('cleanupConfig2Prod').value = record.config2Prod;
            document.getElementById('cleanupRDChecked').value = record.rdChecked;
            document.getElementById('cleanupCFChecked').value = record.cfChecked;
            document.getElementById('cleanupCheckedDate').value = record.checkedDate.split('T')[0];
            document.getElementById('cleanupCCRNumber').value = record.ccrNumber;
            document.getElementById('cleanupJira').value = record.jira;
            document.getElementById('cleanupRepository').value = record.repository;
            document.getElementById('cleanupLASCODE02Path').value = record.lascode02Path;
            document.getElementById('cleanupMovedToDoNotDeploy').value = record.movedToDoNotDeploy;
            document.getElementById('cleanupCommentsNotes').value = record.commentsNotes || '';
            
            openModal('cleanupModal');
        }

        async function saveCleanupRecord(event) {
            event.preventDefault();
            
            const recordId = document.getElementById('cleanupRecordId').value;
            const isEdit = !!recordId;
            
            const data = {
                mwMonth: document.getElementById('cleanupMWMonth').value,
                applicationName: document.getElementById('cleanupApplicationName').value,
                assigned: document.getElementById('cleanupAssigned').value,
                go: document.getElementById('cleanupGo').value,
                ifNoWhy: document.getElementById('cleanupIfNoWhy').value || null,
                ccrChecked: document.getElementById('cleanupCCRChecked').value,
                bin2Prod: document.getElementById('cleanupBin2Prod').value,
                config2Prod: document.getElementById('cleanupConfig2Prod').value,
                rdChecked: document.getElementById('cleanupRDChecked').value,
                cfChecked: document.getElementById('cleanupCFChecked').value,
                checkedDate: document.getElementById('cleanupCheckedDate').value + 'T00:00:00Z',
                ccrNumber: document.getElementById('cleanupCCRNumber').value || null,
                jira: document.getElementById('cleanupJira').value || null,
                repository: document.getElementById('cleanupRepository').value || null,
                lascode02Path: document.getElementById('cleanupLASCODE02Path').value || null,
                movedToDoNotDeploy: document.getElementById('cleanupMovedToDoNotDeploy').value,
                commentsNotes: document.getElementById('cleanupCommentsNotes').value || null
            };
            
            try {
                showLoading(true);
                
                const url = isEdit 
                    ? `${API_BASE_URL}/cleanup/${recordId}`
                    : `${API_BASE_URL}/cleanup`;
                
                const response = await fetchWithAuth(url, {
                    method: isEdit ? 'PUT' : 'POST',
                    body: JSON.stringify(data)
                });
                
                if (!response.ok) {
                    const errorData = await response.json();
                    throw new Error(errorData.error || errorData.title || 'Failed to save record');
                }
                
                showMessage(isEdit ? 'Record updated successfully' : 'Record created successfully', 'success');
                closeModal('cleanupModal');
                await loadCleanupRecords();
                
            } catch (error) {
                console.error('Error saving cleanup record:', error);
                showMessage(error.message || 'Failed to save record', 'error');
            } finally {
                showLoading(false);
            }
        }

        async function deleteCleanupRecord(id) {
            if (!confirm('Are you sure you want to delete this record?')) {
                return;
            }
            
            try {
                showLoading(true);
                
                const response = await fetchWithAuth(`${API_BASE_URL}/cleanup/${id}`, {
                    method: 'DELETE'
                });
                
                if (!response.ok) {
                    throw new Error('Failed to delete record');
                }
                
                showMessage('Record deleted successfully', 'success');
                await loadCleanupRecords();
                
            } catch (error) {
                console.error('Error deleting cleanup record:', error);
                showMessage(error.message || 'Failed to delete record', 'error');
            } finally {
                showLoading(false);
            }
        }

        // ===================================
        // Deployment Record Functions
        // ===================================
        function editDeploymentRecord(id) {
            const record = deploymentRecords.find(r => r.deploymentRecordId === id);
            if (!record) return;
            
            editingRecordId = id;
            document.getElementById('deploymentModalTitle').textContent = 'Edit Deployment Record';
            document.getElementById('deploymentRecordId').value = id;
            document.getElementById('deploymentMWMonth').value = record.mwMonth;
            document.getElementById('deploymentApplicationName').value = record.applicationName;
            document.getElementById('deploymentValidated').value = record.validated;
            document.getElementById('deploymentAssignedTo').value = record.assignedTo;
            document.getElementById('deploymentEnvironment').value = record.environment;
            document.getElementById('deploymentReleaseCreated').value = record.releaseCreated;
            document.getElementById('deploymentReleaseChecked').value = record.releaseChecked;
            document.getElementById('deploymentDeployed').value = record.deployed;
            document.getElementById('deploymentReleaseURL').value = record.releaseURL;
            document.getElementById('deploymentCommentsNotes').value = record.commentsNotes || '';
            
            openModal('deploymentModal');
        }

        async function saveDeploymentRecord(event) {
            event.preventDefault();
            
            const recordId = document.getElementById('deploymentRecordId').value;
            const isEdit = !!recordId;
            
            const data = {
                mwMonth: document.getElementById('deploymentMWMonth').value,
                applicationName: document.getElementById('deploymentApplicationName').value,
                validated: document.getElementById('deploymentValidated').value,
                assignedTo: document.getElementById('deploymentAssignedTo').value,
                environment: document.getElementById('deploymentEnvironment').value,
                releaseCreated: document.getElementById('deploymentReleaseCreated').value,
                releaseChecked: document.getElementById('deploymentReleaseChecked').value,
                deployed: document.getElementById('deploymentDeployed').value,
                releaseURL: document.getElementById('deploymentReleaseURL').value || null,
                commentsNotes: document.getElementById('deploymentCommentsNotes').value || null
            };
            
            try {
                showLoading(true);
                
                const url = isEdit 
                    ? `${API_BASE_URL}/deployment/${recordId}`
                    : `${API_BASE_URL}/deployment`;
                
                const response = await fetchWithAuth(url, {
                    method: isEdit ? 'PUT' : 'POST',
                    body: JSON.stringify(data)
                });
                
                if (!response.ok) {
                    const errorData = await response.json();
                    throw new Error(errorData.error || errorData.title || 'Failed to save record');
                }
                
                showMessage(isEdit ? 'Record updated successfully' : 'Record created successfully', 'success');
                closeModal('deploymentModal');
                await loadDeploymentRecords();
                
            } catch (error) {
                console.error('Error saving deployment record:', error);
                showMessage(error.message || 'Failed to save record', 'error');
            } finally {
                showLoading(false);
            }
        }

        async function deleteDeploymentRecord(id) {
            if (!confirm('Are you sure you want to delete this record?')) {
                return;
            }
            
            try {
                showLoading(true);
                
                const response = await fetchWithAuth(`${API_BASE_URL}/deployment/${id}`, {
                    method: 'DELETE'
                });
                
                if (!response.ok) {
                    throw new Error('Failed to delete record');
                }
                
                showMessage('Record deleted successfully', 'success');
                await loadDeploymentRecords();
                
            } catch (error) {
                console.error('Error deleting deployment record:', error);
                showMessage(error.message || 'Failed to delete record', 'error');
            } finally {
                showLoading(false);
            }
        }

        // ===================================
        // CSV Export Function
        // ===================================
        function exportToCSV() {
            const month = document.getElementById('monthSelect').value;
            
            if (!month) {
                showMessage('Please select a month first', 'error');
                return;
            }
            
            let csvContent = '';
            let filename = '';
            
            if (currentTab === 'cleanup') {
                if (cleanupRecords.length === 0) {
                    showMessage('No cleanup records to export', 'error');
                    return;
                }
                
                // CSV Headers for Cleanup
                csvContent = 'Application Name,Assigned,Go,If No Why,CCR Checked,Bin2Prod,Config2Prod,RD Checked,CF Checked,Checked Date,CCR Number,Jira,Repository,LASCODE02 Path,Moved To DoNotDeploy,Comments/Notes\n';
                
                // CSV Data for Cleanup
                cleanupRecords.forEach(record => {
                    const row = [
                        escapeCSV(record.applicationName),
                        escapeCSV(record.assigned),
                        escapeCSV(record.go),
                        escapeCSV(record.ifNoWhy),
                        escapeCSV(record.ccrChecked),
                        escapeCSV(record.bin2Prod),
                        escapeCSV(record.config2Prod),
                        escapeCSV(record.rdChecked),
                        escapeCSV(record.cfChecked),
                        escapeCSV(record.checkedDate ? record.checkedDate.split('T')[0] : ''),
                        escapeCSV(record.ccrNumber),
                        escapeCSV(record.jira),
                        escapeCSV(record.repository),
                        escapeCSV(record.lascode02Path),
                        escapeCSV(record.movedToDoNotDeploy),
                        escapeCSV(record.commentsNotes)
                    ];
                    csvContent += row.join(',') + '\n';
                });
                
                filename = `Cleanup_Records_${month.replace(' ', '_')}_${new Date().toISOString().split('T')[0]}.csv`;
                
            } else {
                if (deploymentRecords.length === 0) {
                    showMessage('No deployment records to export', 'error');
                    return;
                }
                
                // CSV Headers for Deployment
                csvContent = 'Application Name,Validated,Assigned To,Environment,Release Created,Release Checked,Deployed,Release URL,Comments/Notes\n';
                
                // CSV Data for Deployment
                deploymentRecords.forEach(record => {
                    const row = [
                        escapeCSV(record.applicationName),
                        escapeCSV(record.validated),
                        escapeCSV(record.assignedTo),
                        escapeCSV(record.environment),
                        escapeCSV(record.releaseCreated),
                        escapeCSV(record.releaseChecked),
                        escapeCSV(record.deployed),
                        escapeCSV(record.releaseURL),
                        escapeCSV(record.commentsNotes)
                    ];
                    csvContent += row.join(',') + '\n';
                });
                
                filename = `Deployment_Records_${month.replace(' ', '_')}_${new Date().toISOString().split('T')[0]}.csv`;
            }
            
            // Create and download CSV file
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const url = window.URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = filename;
            document.body.appendChild(link);
            link.click();
            
            setTimeout(() => {
                window.URL.revokeObjectURL(url);
                document.body.removeChild(link);
                showMessage(`✅ CSV exported successfully: ${filename}`, 'success');
            }, 100);
        }

        function escapeCSV(value) {
            if (value === null || value === undefined) {
                return '""';
            }
            
            const stringValue = String(value);
            
            // If the value contains comma, quote, or newline, wrap it in quotes
            if (stringValue.includes(',') || stringValue.includes('"') || stringValue.includes('\n')) {
                // Escape quotes by doubling them
                return '"' + stringValue.replace(/"/g, '""') + '"';
            }
            
            return stringValue;
        }

        // ===================================
        // Utility Functions
        // ===================================
        function downloadProjectFiles() {
            const projectStructure = `
MW MANAGEMENT SYSTEM - C# REST API PROJECT WITH AUDIT TRAIL
============================================================

PROJECT STRUCTURE:
------------------
MWManagementAPI/
├── Controllers/
│   ├── AuthController.cs
│   ├── CleanupController.cs
│   ├── DeploymentController.cs
│   ├── MasterDataController.cs
│   └── AuditController.cs
├── Models/
│   ├── User.cs
│   ├── CleanupRecord.cs
│   ├── DeploymentRecord.cs
│   ├── AuditLog.cs
│   ├── ApplicationMaster.cs
│   ├── MWMonthMaster.cs
│   ├── LASCodePathMaster.cs
│   ├── LoginRequest.cs
│   ├── RegisterRequest.cs
│   └── AuthResponse.cs
├── Data/
│   └── ApplicationDbContext.cs
├── Services/
│   ├── IAuthService.cs
│   ├── AuthService.cs
│   ├── IAuditService.cs
│   └── AuditService.cs
├── appsettings.json
└── Program.cs

DATABASE SCRIPT:
================

-- Create Database
CREATE DATABASE MWManagementDB;
GO

USE MWManagementDB;
GO

-- Users Table
CREATE TABLE Users (
    UserId INT PRIMARY KEY IDENTITY(1,1),
    Username NVARCHAR(50) NOT NULL UNIQUE,
    Email NVARCHAR(100) NOT NULL UNIQUE,
    FullName NVARCHAR(100) NOT NULL,
    PasswordHash NVARCHAR(255) NOT NULL,
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CONSTRAINT CHK_Username_Length CHECK (LEN(Username) >= 3),
    CONSTRAINT CHK_Email_Format CHECK (Email LIKE '%@%.%')
);

-- =====================================================
-- MASTER DATA TABLES
-- =====================================================

-- Application Master Table
CREATE TABLE ApplicationMaster (
    ApplicationId INT PRIMARY KEY IDENTITY(1,1),
    ApplicationName NVARCHAR(200) NOT NULL UNIQUE,
    IsActive BIT DEFAULT 1,
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CreatedBy INT NOT NULL,
    CONSTRAINT FK_ApplicationMaster_CreatedBy FOREIGN KEY (CreatedBy) REFERENCES Users(UserId)
);

-- MW Month Master Table
CREATE TABLE MWMonthMaster (
    MWMonthId INT PRIMARY KEY IDENTITY(1,1),
    MWMonth NVARCHAR(50) NOT NULL UNIQUE,
    IsActive BIT DEFAULT 1,
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CreatedBy INT NOT NULL,
    CONSTRAINT FK_MWMonthMaster_CreatedBy FOREIGN KEY (CreatedBy) REFERENCES Users(UserId)
);

-- LASCode Path Master Table
CREATE TABLE LASCodePathMaster (
    LASCodePathId INT PRIMARY KEY IDENTITY(1,1),
    LASCodePath NVARCHAR(500) NOT NULL UNIQUE,
    IsActive BIT DEFAULT 1,
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CreatedBy INT NOT NULL,
    CONSTRAINT FK_LASCodePathMaster_CreatedBy FOREIGN KEY (CreatedBy) REFERENCES Users(UserId)
);

-- =====================================================
-- CLEANUP RECORDS TABLE (Updated with Foreign Keys)
-- =====================================================
CREATE TABLE CleanupRecords (
    CleanupRecordId INT PRIMARY KEY IDENTITY(1,1),
    ApplicationId INT NOT NULL,
    MWMonthId INT NOT NULL,
    Assigned NVARCHAR(100) NOT NULL,
    [Go] NVARCHAR(10) NOT NULL,
    IfNoWhy NVARCHAR(500),
    CCRChecked NVARCHAR(10) NOT NULL,
    Bin2Prod NVARCHAR(10) NOT NULL,
    Config2Prod NVARCHAR(10) NOT NULL,
    RDChecked NVARCHAR(10) NOT NULL,
    CFChecked NVARCHAR(10) NOT NULL,
    CheckedDate DATE NOT NULL,
    CCRNumber NVARCHAR(50),
    Jira NVARCHAR(50),
    Repository NVARCHAR(500),
    LASCodePathId INT,
    MovedToDoNotDeploy NVARCHAR(10) NOT NULL,
    CommentsNotes NVARCHAR(1000),
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CreatedBy INT NOT NULL,
    UpdatedAt DATETIME2 DEFAULT GETDATE(),
    UpdatedBy INT NOT NULL,
    CONSTRAINT FK_CleanupRecords_Application FOREIGN KEY (ApplicationId) REFERENCES ApplicationMaster(ApplicationId),
    CONSTRAINT FK_CleanupRecords_MWMonth FOREIGN KEY (MWMonthId) REFERENCES MWMonthMaster(MWMonthId),
    CONSTRAINT FK_CleanupRecords_LASCodePath FOREIGN KEY (LASCodePathId) REFERENCES LASCodePathMaster(LASCodePathId),
    CONSTRAINT FK_CleanupRecords_CreatedBy FOREIGN KEY (CreatedBy) REFERENCES Users(UserId),
    CONSTRAINT FK_CleanupRecords_UpdatedBy FOREIGN KEY (UpdatedBy) REFERENCES Users(UserId)
);

-- =====================================================
-- DEPLOYMENT RECORDS TABLE (Updated with Foreign Keys)
-- =====================================================
CREATE TABLE DeploymentRecords (
    DeploymentRecordId INT PRIMARY KEY IDENTITY(1,1),
    ApplicationId INT NOT NULL,
    MWMonthId INT NOT NULL,
    Validated NVARCHAR(10) NOT NULL,
    AssignedTo NVARCHAR(100) NOT NULL,
    Environment NVARCHAR(10) NOT NULL,
    ReleaseCreated NVARCHAR(10) NOT NULL,
    ReleaseChecked NVARCHAR(10) NOT NULL,
    Deployed NVARCHAR(10) NOT NULL,
    ReleaseURL NVARCHAR(500),
    CommentsNotes NVARCHAR(1000),
    CreatedAt DATETIME2 DEFAULT GETDATE(),
    CreatedBy INT NOT NULL,
    UpdatedAt DATETIME2 DEFAULT GETDATE(),
    UpdatedBy INT NOT NULL,
    CONSTRAINT FK_DeploymentRecords_Application FOREIGN KEY (ApplicationId) REFERENCES ApplicationMaster(ApplicationId),
    CONSTRAINT FK_DeploymentRecords_MWMonth FOREIGN KEY (MWMonthId) REFERENCES MWMonthMaster(MWMonthId),
    CONSTRAINT FK_DeploymentRecords_CreatedBy FOREIGN KEY (CreatedBy) REFERENCES Users(UserId),
    CONSTRAINT FK_DeploymentRecords_UpdatedBy FOREIGN KEY (UpdatedBy) REFERENCES Users(UserId)
);

-- =====================================================
-- AUDIT LOG TABLE (Complete History Tracking)
-- =====================================================
CREATE TABLE AuditLogs (
    AuditId INT PRIMARY KEY IDENTITY(1,1),
    TableName NVARCHAR(100) NOT NULL,
    RecordId INT NOT NULL,
    Action NVARCHAR(20) NOT NULL, -- CREATE, UPDATE, DELETE
    FieldName NVARCHAR(100),
    OldValue NVARCHAR(MAX),
    NewValue NVARCHAR(MAX),
    ChangedBy INT NOT NULL,
    ChangedByUsername NVARCHAR(50) NOT NULL,
    ChangedByFullName NVARCHAR(100) NOT NULL,
    ChangedAt DATETIME2 DEFAULT GETDATE(),
    CONSTRAINT FK_AuditLogs_User FOREIGN KEY (ChangedBy) REFERENCES Users(UserId)
);

-- Create Indexes for Performance
CREATE INDEX IX_CleanupRecords_ApplicationId ON CleanupRecords(ApplicationId);
CREATE INDEX IX_CleanupRecords_MWMonthId ON CleanupRecords(MWMonthId);
CREATE INDEX IX_CleanupRecords_LASCodePathId ON CleanupRecords(LASCodePathId);
CREATE INDEX IX_DeploymentRecords_ApplicationId ON DeploymentRecords(ApplicationId);
CREATE INDEX IX_DeploymentRecords_MWMonthId ON DeploymentRecords(MWMonthId);
CREATE INDEX IX_AuditLogs_TableName_RecordId ON AuditLogs(TableName, RecordId);
CREATE INDEX IX_AuditLogs_ChangedAt ON AuditLogs(ChangedAt DESC);
CREATE INDEX IX_AuditLogs_ChangedBy ON AuditLogs(ChangedBy);

-- Insert Sample Master Data
INSERT INTO ApplicationMaster (ApplicationName, IsActive, CreatedAt, CreatedBy)
VALUES 
    ('Sample Application 1', 1, GETDATE(), 1),
    ('Sample Application 2', 1, GETDATE(), 1);

INSERT INTO MWMonthMaster (MWMonth, IsActive, CreatedAt, CreatedBy)
VALUES 
    ('January 2024', 1, GETDATE(), 1),
    ('February 2024', 1, GETDATE(), 1),
    ('March 2024', 1, GETDATE(), 1);

INSERT INTO LASCodePathMaster (LASCodePath, IsActive, CreatedAt, CreatedBy)
VALUES 
    ('\\LASCODE02\\Path1', 1, GETDATE(), 1),
    ('\\LASCODE02\\Path2', 1, GETDATE(), 1);

GO

================================================================================

FILE: Models/AuditLog.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("AuditLogs")]
    public class AuditLog
    {
        [Key]
        public int AuditId { get; set; }

        [Required]
        [MaxLength(100)]
        public string TableName { get; set; }

        [Required]
        public int RecordId { get; set; }

        [Required]
        [MaxLength(20)]
        public string Action { get; set; } // CREATE, UPDATE, DELETE

        [MaxLength(100)]
        public string? FieldName { get; set; }

        public string? OldValue { get; set; }

        public string? NewValue { get; set; }

        [Required]
        public int ChangedBy { get; set; }

        [Required]
        [MaxLength(50)]
        public string ChangedByUsername { get; set; }

        [Required]
        [MaxLength(100)]
        public string ChangedByFullName { get; set; }

        public DateTime ChangedAt { get; set; } = DateTime.UtcNow;

        // Navigation Property
        [ForeignKey("ChangedBy")]
        public virtual User? User { get; set; }
    }
}

================================================================================

FILE: Models/ApplicationMaster.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("ApplicationMaster")]
    public class ApplicationMaster
    {
        [Key]
        public int ApplicationId { get; set; }

        [Required]
        [MaxLength(200)]
        public string ApplicationName { get; set; }

        public bool IsActive { get; set; } = true;

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        [Required]
        public int CreatedBy { get; set; }

        // Navigation Properties
        [ForeignKey("CreatedBy")]
        public virtual User? User { get; set; }

        public virtual ICollection<CleanupRecord>? CleanupRecords { get; set; }
        public virtual ICollection<DeploymentRecord>? DeploymentRecords { get; set; }
    }
}

================================================================================

FILE: Models/MWMonthMaster.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("MWMonthMaster")]
    public class MWMonthMaster
    {
        [Key]
        public int MWMonthId { get; set; }

        [Required]
        [MaxLength(50)]
        public string MWMonth { get; set; }

        public bool IsActive { get; set; } = true;

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        [Required]
        public int CreatedBy { get; set; }

        // Navigation Properties
        [ForeignKey("CreatedBy")]
        public virtual User? User { get; set; }

        public virtual ICollection<CleanupRecord>? CleanupRecords { get; set; }
        public virtual ICollection<DeploymentRecord>? DeploymentRecords { get; set; }
    }
}

================================================================================

FILE: Models/LASCodePathMaster.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("LASCodePathMaster")]
    public class LASCodePathMaster
    {
        [Key]
        public int LASCodePathId { get; set; }

        [Required]
        [MaxLength(500)]
        public string LASCodePath { get; set; }

        public bool IsActive { get; set; } = true;

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        [Required]
        public int CreatedBy { get; set; }

        // Navigation Properties
        [ForeignKey("CreatedBy")]
        public virtual User? User { get; set; }

        public virtual ICollection<CleanupRecord>? CleanupRecords { get; set; }
    }
}

================================================================================

using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.EntityFrameworkCore;
using Microsoft.IdentityModel.Tokens;
using MWManagementAPI.Data;
using MWManagementAPI.Services;
using System.Text;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Database Configuration
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// JWT Authentication Configuration
var jwtSettings = builder.Configuration.GetSection("JwtSettings");
var secretKey = jwtSettings["SecretKey"];

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = jwtSettings["Issuer"],
            ValidAudience = jwtSettings["Audience"],
            IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey))
        };
    });

// Register Services
builder.Services.AddScoped<IAuthService, AuthService>();
builder.Services.AddScoped<IAuditService, AuditService>();

// CORS Configuration
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll",
        builder =>
        {
            builder.AllowAnyOrigin()
                   .AllowAnyMethod()
                   .AllowAnyHeader();
        });
});

var app = builder.Build();

// Configure the HTTP request pipeline
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();
app.UseCors("AllowAll");
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();

================================================================================

FILE: Services/IAuditService.cs
================================================================================

using MWManagementAPI.Models;

namespace MWManagementAPI.Services
{
    public interface IAuditService
    {
        Task LogCreateAsync(string tableName, int recordId, object newRecord, int userId, string username, string fullName);
        Task LogUpdateAsync(string tableName, int recordId, object oldRecord, object newRecord, int userId, string username, string fullName);
        Task LogDeleteAsync(string tableName, int recordId, object oldRecord, int userId, string username, string fullName);
        Task<List<AuditLog>> GetAuditHistoryAsync(string tableName, int recordId);
    }
}

================================================================================

FILE: Services/AuditService.cs
================================================================================

using Microsoft.EntityFrameworkCore;
using MWManagementAPI.Data;
using MWManagementAPI.Models;
using System.Reflection;
using System.Text.Json;

namespace MWManagementAPI.Services
{
    public class AuditService : IAuditService
    {
        private readonly ApplicationDbContext _context;

        public AuditService(ApplicationDbContext context)
        {
            _context = context;
        }

        public async Task LogCreateAsync(string tableName, int recordId, object newRecord, int userId, string username, string fullName)
        {
            var properties = newRecord.GetType().GetProperties(BindingFlags.Public | BindingFlags.Instance);

            foreach (var prop in properties)
            {
                var value = prop.GetValue(newRecord);
                if (value != null && !IsNavigationProperty(prop))
                {
                    var auditLog = new AuditLog
                    {
                        TableName = tableName,
                        RecordId = recordId,
                        Action = "CREATE",
                        FieldName = prop.Name,
                        OldValue = null,
                        NewValue = SerializeValue(value),
                        ChangedBy = userId,
                        ChangedByUsername = username,
                        ChangedByFullName = fullName,
                        ChangedAt = DateTime.UtcNow
                    };

                    _context.AuditLogs.Add(auditLog);
                }
            }

            await _context.SaveChangesAsync();
        }

        public async Task LogUpdateAsync(string tableName, int recordId, object oldRecord, object newRecord, int userId, string username, string fullName)
        {
            var properties = newRecord.GetType().GetProperties(BindingFlags.Public | BindingFlags.Instance);

            foreach (var prop in properties)
            {
                if (IsNavigationProperty(prop))
                    continue;

                var oldValue = prop.GetValue(oldRecord);
                var newValue = prop.GetValue(newRecord);

                var oldValueStr = SerializeValue(oldValue);
                var newValueStr = SerializeValue(newValue);

                if (oldValueStr != newValueStr)
                {
                    var auditLog = new AuditLog
                    {
                        TableName = tableName,
                        RecordId = recordId,
                        Action = "UPDATE",
                        FieldName = prop.Name,
                        OldValue = oldValueStr,
                        NewValue = newValueStr,
                        ChangedBy = userId,
                        ChangedByUsername = username,
                        ChangedByFullName = fullName,
                        ChangedAt = DateTime.UtcNow
                    };

                    _context.AuditLogs.Add(auditLog);
                }
            }

            await _context.SaveChangesAsync();
        }

        public async Task LogDeleteAsync(string tableName, int recordId, object oldRecord, int userId, string username, string fullName)
        {
            var properties = oldRecord.GetType().GetProperties(BindingFlags.Public | BindingFlags.Instance);

            foreach (var prop in properties)
            {
                var value = prop.GetValue(oldRecord);
                if (value != null && !IsNavigationProperty(prop))
                {
                    var auditLog = new AuditLog
                    {
                        TableName = tableName,
                        RecordId = recordId,
                        Action = "DELETE",
                        FieldName = prop.Name,
                        OldValue = SerializeValue(value),
                        NewValue = null,
                        ChangedBy = userId,
                        ChangedByUsername = username,
                        ChangedByFullName = fullName,
                        ChangedAt = DateTime.UtcNow
                    };

                    _context.AuditLogs.Add(auditLog);
                }
            }

            await _context.SaveChangesAsync();
        }

        public async Task<List<AuditLog>> GetAuditHistoryAsync(string tableName, int recordId)
        {
            return await _context.AuditLogs
                .Where(a => a.TableName == tableName && a.RecordId == recordId)
                .OrderByDescending(a => a.ChangedAt)
                .ToListAsync();
        }

        private bool IsNavigationProperty(PropertyInfo property)
        {
            return typeof(System.Collections.IEnumerable).IsAssignableFrom(property.PropertyType) && property.PropertyType != typeof(string)
                || property.PropertyType.IsClass && property.PropertyType != typeof(string) && !property.PropertyType.IsValueType;
        }

        private string SerializeValue(object? value)
        {
            if (value == null)
                return "null";

            if (value is DateTime dateTime)
                return dateTime.ToString("yyyy-MM-dd HH:mm:ss");

            return value.ToString() ?? "null";
        }
    }
}

================================================================================

FILE: Data/ApplicationDbContext.cs
================================================================================

using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.EntityFrameworkCore;
using Microsoft.IdentityModel.Tokens;
using MWManagementAPI.Data;
using MWManagementAPI.Services;
using System.Text;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Database Configuration
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// JWT Authentication Configuration
var jwtSettings = builder.Configuration.GetSection("JwtSettings");
var secretKey = jwtSettings["SecretKey"];

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = jwtSettings["Issuer"],
            ValidAudience = jwtSettings["Audience"],
            IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey))
        };
    });

// Register Services
builder.Services.AddScoped<IAuthService, AuthService>();

// CORS Configuration
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll",
        builder =>
        {
            builder.AllowAnyOrigin()
                   .AllowAnyMethod()
                   .AllowAnyHeader();
        });
});

var app = builder.Build();

// Configure the HTTP request pipeline
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();
app.UseCors("AllowAll");
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();

================================================================================

FILE: appsettings.json
================================================================================

{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=MWManagementDB;Trusted_Connection=True;TrustServerCertificate=True;"
  },
  "JwtSettings": {
    "SecretKey": "YourSuperSecretKeyThatIsAtLeast32CharactersLong!",
    "Issuer": "MWManagementAPI",
    "Audience": "MWManagementClient",
    "ExpiresInMinutes": 480
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}

================================================================================

FILE: Data/ApplicationDbContext.cs
================================================================================

using Microsoft.EntityFrameworkCore;
using MWManagementAPI.Models;

namespace MWManagementAPI.Data
{
    public class ApplicationDbContext : DbContext
    {
        public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options)
            : base(options)
        {
        }

        public DbSet<User> Users { get; set; }
        public DbSet<CleanupRecord> CleanupRecords { get; set; }
        public DbSet<DeploymentRecord> DeploymentRecords { get; set; }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            base.OnModelCreating(modelBuilder);

            // User Configuration
            modelBuilder.Entity<User>(entity =>
            {
                entity.HasKey(e => e.UserId);
                entity.Property(e => e.Username).IsRequired().HasMaxLength(50);
                entity.Property(e => e.Email).IsRequired().HasMaxLength(100);
                entity.Property(e => e.FullName).IsRequired().HasMaxLength(100);
                entity.Property(e => e.PasswordHash).IsRequired().HasMaxLength(255);
                entity.HasIndex(e => e.Username).IsUnique();
                entity.HasIndex(e => e.Email).IsUnique();
            });

            // CleanupRecord Configuration
            modelBuilder.Entity<CleanupRecord>(entity =>
            {
                entity.HasKey(e => e.CleanupRecordId);
                entity.Property(e => e.MWMonth).IsRequired().HasMaxLength(50);
                entity.Property(e => e.ApplicationName).IsRequired().HasMaxLength(200);
                entity.HasOne(e => e.User)
                    .WithMany(u => u.CleanupRecords)
                    .HasForeignKey(e => e.UserId)
                    .OnDelete(DeleteBehavior.Cascade);
            });

            // DeploymentRecord Configuration
            modelBuilder.Entity<DeploymentRecord>(entity =>
            {
                entity.HasKey(e => e.DeploymentRecordId);
                entity.Property(e => e.MWMonth).IsRequired().HasMaxLength(50);
                entity.Property(e => e.ApplicationName).IsRequired().HasMaxLength(200);
                entity.HasOne(e => e.User)
                    .WithMany(u => u.DeploymentRecords)
                    .HasForeignKey(e => e.UserId)
                    .OnDelete(DeleteBehavior.Cascade);
            });
        }
    }
}

================================================================================

FILE: Models/User.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("Users")]
    public class User
    {
        [Key]
        public int UserId { get; set; }

        [Required]
        [MaxLength(50)]
        public string Username { get; set; }

        [Required]
        [MaxLength(100)]
        [EmailAddress]
        public string Email { get; set; }

        [Required]
        [MaxLength(100)]
        public string FullName { get; set; }

        [Required]
        [MaxLength(255)]
        public string PasswordHash { get; set; }

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        // Navigation Properties
        public virtual ICollection<CleanupRecord> CleanupRecords { get; set; }
        public virtual ICollection<DeploymentRecord> DeploymentRecords { get; set; }
    }
}

================================================================================

FILE: Models/CleanupRecord.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("CleanupRecords")]
    public class CleanupRecord
    {
        [Key]
        public int CleanupRecordId { get; set; }

        [Required]
        public int UserId { get; set; }

        [Required]
        [MaxLength(50)]
        public string MWMonth { get; set; }

        [Required]
        [MaxLength(200)]
        public string ApplicationName { get; set; }

        [Required]
        [MaxLength(100)]
        public string Assigned { get; set; }

        [Required]
        [MaxLength(10)]
        [Column("Go")]
        public string Go { get; set; }

        [MaxLength(500)]
        public string? IfNoWhy { get; set; }

        [Required]
        [MaxLength(10)]
        public string CCRChecked { get; set; }

        [Required]
        [MaxLength(10)]
        public string Bin2Prod { get; set; }

        [Required]
        [MaxLength(10)]
        public string Config2Prod { get; set; }

        [Required]
        [MaxLength(10)]
        public string RDChecked { get; set; }

        [Required]
        [MaxLength(10)]
        public string CFChecked { get; set; }

        [Required]
        public DateTime CheckedDate { get; set; }

        [MaxLength(50)]
        public string? CCRNumber { get; set; }

        [MaxLength(50)]
        public string? Jira { get; set; }

        [MaxLength(500)]
        public string? Repository { get; set; }

        [MaxLength(500)]
        public string? LASCODE02Path { get; set; }

        [Required]
        [MaxLength(10)]
        public string MovedToDoNotDeploy { get; set; }

        [MaxLength(1000)]
        public string? CommentsNotes { get; set; }

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        public DateTime UpdatedAt { get; set; } = DateTime.UtcNow;

        // Navigation Property
        [ForeignKey("UserId")]
        public virtual User? User { get; set; }
    }
}

================================================================================

FILE: Models/DeploymentRecord.cs
================================================================================

using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;

namespace MWManagementAPI.Models
{
    [Table("DeploymentRecords")]
    public class DeploymentRecord
    {
        [Key]
        public int DeploymentRecordId { get; set; }

        [Required]
        public int UserId { get; set; }

        [Required]
        [MaxLength(50)]
        public string MWMonth { get; set; }

        [Required]
        [MaxLength(200)]
        public string ApplicationName { get; set; }

        [Required]
        [MaxLength(10)]
        public string Validated { get; set; }

        [Required]
        [MaxLength(100)]
        public string AssignedTo { get; set; }

        [Required]
        [MaxLength(10)]
        public string Environment { get; set; }

        [Required]
        [MaxLength(10)]
        public string ReleaseCreated { get; set; }

        [Required]
        [MaxLength(10)]
        public string ReleaseChecked { get; set; }

        [Required]
        [MaxLength(10)]
        public string Deployed { get; set; }

        [MaxLength(500)]
        public string? ReleaseURL { get; set; }

        [MaxLength(1000)]
        public string? CommentsNotes { get; set; }

        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;

        public DateTime UpdatedAt { get; set; } = DateTime.UtcNow;

        // Navigation Property
        [ForeignKey("UserId")]
        public virtual User? User { get; set; }
    }
}

================================================================================

FILE: Models/LoginRequest.cs
================================================================================

using System.ComponentModel.DataAnnotations;

namespace MWManagementAPI.Models
{
    public class LoginRequest
    {
        [Required]
        public string Username { get; set; }

        [Required]
        public string Password { get; set; }
    }
}

================================================================================

FILE: Models/RegisterRequest.cs
================================================================================

using System.ComponentModel.DataAnnotations;

namespace MWManagementAPI.Models
{
    public class RegisterRequest
    {
        [Required]
        [MinLength(3)]
        [MaxLength(50)]
        public string Username { get; set; }

        [Required]
        [EmailAddress]
        [MaxLength(100)]
        public string Email { get; set; }

        [Required]
        [MaxLength(100)]
        public string FullName { get; set; }

        [Required]
        [MinLength(6)]
        public string Password { get; set; }
    }
}

================================================================================

FILE: Models/AuthResponse.cs
================================================================================

namespace MWManagementAPI.Models
{
    public class AuthResponse
    {
        public string Token { get; set; }
        public int UserId { get; set; }
        public string Username { get; set; }
        public string FullName { get; set; }
        public DateTime ExpiresAt { get; set; }
    }
}

================================================================================

FILE: Services/IAuthService.cs
================================================================================

using MWManagementAPI.Models;

namespace MWManagementAPI.Services
{
    public interface IAuthService
    {
        Task<AuthResponse> RegisterAsync(RegisterRequest request);
        Task<AuthResponse> LoginAsync(LoginRequest request);
        string GenerateJwtToken(User user);
        string HashPassword(string password);
        bool VerifyPassword(string password, string passwordHash);
    }
}

================================================================================

FILE: Services/AuthService.cs
================================================================================

using Microsoft.EntityFrameworkCore;
using Microsoft.IdentityModel.Tokens;
using MWManagementAPI.Data;
using MWManagementAPI.Models;
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using System.Security.Cryptography;
using System.Text;

namespace MWManagementAPI.Services
{
    public class AuthService : IAuthService
    {
        private readonly ApplicationDbContext _context;
        private readonly IConfiguration _configuration;

        public AuthService(ApplicationDbContext context, IConfiguration configuration)
        {
            _context = context;
            _configuration = configuration;
        }

        public async Task<AuthResponse> RegisterAsync(RegisterRequest request)
        {
            // Check if username exists
            if (await _context.Users.AnyAsync(u => u.Username == request.Username))
            {
                throw new Exception("Username already exists");
            }

            // Check if email exists
            if (await _context.Users.AnyAsync(u => u.Email == request.Email))
            {
                throw new Exception("Email already exists");
            }

            // Create new user
            var user = new User
            {
                Username = request.Username,
                Email = request.Email,
                FullName = request.FullName,
                PasswordHash = HashPassword(request.Password),
                CreatedAt = DateTime.UtcNow
            };

            _context.Users.Add(user);
            await _context.SaveChangesAsync();

            // Generate token
            var token = GenerateJwtToken(user);
            var expiresInMinutes = int.Parse(_configuration["JwtSettings:ExpiresInMinutes"]);

            return new AuthResponse
            {
                Token = token,
                UserId = user.UserId,
                Username = user.Username,
                FullName = user.FullName,
                ExpiresAt = DateTime.UtcNow.AddMinutes(expiresInMinutes)
            };
        }

        public async Task<AuthResponse> LoginAsync(LoginRequest request)
        {
            var user = await _context.Users
                .FirstOrDefaultAsync(u => u.Username == request.Username);

            if (user == null || !VerifyPassword(request.Password, user.PasswordHash))
            {
                throw new Exception("Invalid username or password");
            }

            var token = GenerateJwtToken(user);
            var expiresInMinutes = int.Parse(_configuration["JwtSettings:ExpiresInMinutes"]);

            return new AuthResponse
            {
                Token = token,
                UserId = user.UserId,
                Username = user.Username,
                FullName = user.FullName,
                ExpiresAt = DateTime.UtcNow.AddMinutes(expiresInMinutes)
            };
        }

        public string GenerateJwtToken(User user)
        {
            var jwtSettings = _configuration.GetSection("JwtSettings");
            var secretKey = jwtSettings["SecretKey"];
            var issuer = jwtSettings["Issuer"];
            var audience = jwtSettings["Audience"];
            var expiresInMinutes = int.Parse(jwtSettings["ExpiresInMinutes"]);

            var securityKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey));
            var credentials = new SigningCredentials(securityKey, SecurityAlgorithms.HmacSha256);

            var claims = new[]
            {
                new Claim(JwtRegisteredClaimNames.Sub, user.UserId.ToString()),
                new Claim(JwtRegisteredClaimNames.UniqueName, user.Username),
                new Claim(ClaimTypes.Name, user.FullName),
                new Claim(JwtRegisteredClaimNames.Jti, Guid.NewGuid().ToString())
            };

            var token = new JwtSecurityToken(
                issuer: issuer,
                audience: audience,
                claims: claims,
                expires: DateTime.UtcNow.AddMinutes(expiresInMinutes),
                signingCredentials: credentials
            );

            return new JwtSecurityTokenHandler().WriteToken(token);
        }

        public string HashPassword(string password)
        {
            using (var sha256 = SHA256.Create())
            {
                var hashedBytes = sha256.ComputeHash(Encoding.UTF8.GetBytes(password));
                return Convert.ToBase64String(hashedBytes);
            }
        }

        public bool VerifyPassword(string password, string passwordHash)
        {
            var hashedInput = HashPassword(password);
            return hashedInput == passwordHash;
        }
    }
}

================================================================================

FILE: Controllers/AuthController.cs
================================================================================

using Microsoft.AspNetCore.Mvc;
using MWManagementAPI.Models;
using MWManagementAPI.Services;

namespace MWManagementAPI.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class AuthController : ControllerBase
    {
        private readonly IAuthService _authService;

        public AuthController(IAuthService authService)
        {
            _authService = authService;
        }

        [HttpPost("register")]
        public async Task<IActionResult> Register([FromBody] RegisterRequest request)
        {
            try
            {
                var response = await _authService.RegisterAsync(request);
                return Ok(response);
            }
            catch (Exception ex)
            {
                return BadRequest(new { error = ex.Message });
            }
        }

        [HttpPost("login")]
        public async Task<IActionResult> Login([FromBody] LoginRequest request)
        {
            try
            {
                var response = await _authService.LoginAsync(request);
                return Ok(response);
            }
            catch (Exception ex)
            {
                return Unauthorized(new { error = ex.Message });
            }
        }
    }
}

================================================================================

FILE: Controllers/CleanupController.cs
================================================================================

using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using MWManagementAPI.Data;
using MWManagementAPI.Models;
using System.Security.Claims;

namespace MWManagementAPI.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    [Authorize]
    public class CleanupController : ControllerBase
    {
        private readonly ApplicationDbContext _context;

        public CleanupController(ApplicationDbContext context)
        {
            _context = context;
        }

        private int GetUserId()
        {
            var userIdClaim = User.FindFirst(ClaimTypes.NameIdentifier)?.Value;
            return int.Parse(userIdClaim);
        }

        // GET: api/cleanup?mwMonth=January 2024
        [HttpGet]
        public async Task<ActionResult<IEnumerable<CleanupRecord>>> GetCleanupRecords([FromQuery] string mwMonth)
        {
            var userId = GetUserId();

            var records = await _context.CleanupRecords
                .Where(r => r.UserId == userId && r.MWMonth == mwMonth)
                .OrderByDescending(r => r.CreatedAt)
                .ToListAsync();

            return Ok(records);
        }

        // GET: api/cleanup/5
        [HttpGet("{id}")]
        public async Task<ActionResult<CleanupRecord>> GetCleanupRecord(int id)
        {
            var userId = GetUserId();
            var record = await _context.CleanupRecords
                .FirstOrDefaultAsync(r => r.CleanupRecordId == id && r.UserId == userId);

            if (record == null)
            {
                return NotFound();
            }

            return Ok(record);
        }

        // POST: api/cleanup
        [HttpPost]
        public async Task<ActionResult<CleanupRecord>> CreateCleanupRecord([FromBody] CleanupRecord record)
        {
            try
            {
                var userId = GetUserId();
                
                // Set user ID and timestamps
                record.UserId = userId;
                record.CreatedAt = DateTime.UtcNow;
                record.UpdatedAt = DateTime.UtcNow;
                
                // Validate required fields
                if (string.IsNullOrWhiteSpace(record.MWMonth) ||
                    string.IsNullOrWhiteSpace(record.ApplicationName) ||
                    string.IsNullOrWhiteSpace(record.Assigned) ||
                    string.IsNullOrWhiteSpace(record.Go) ||
                    string.IsNullOrWhiteSpace(record.CCRChecked) ||
                    string.IsNullOrWhiteSpace(record.Bin2Prod) ||
                    string.IsNullOrWhiteSpace(record.Config2Prod) ||
                    string.IsNullOrWhiteSpace(record.RDChecked) ||
                    string.IsNullOrWhiteSpace(record.CFChecked) ||
                    string.IsNullOrWhiteSpace(record.MovedToDoNotDeploy))
                {
                    return BadRequest(new { error = "All required fields must be filled" });
                }

                _context.CleanupRecords.Add(record);
                await _context.SaveChangesAsync();

                return CreatedAtAction(nameof(GetCleanupRecord), new { id = record.CleanupRecordId }, record);
            }
            catch (Exception ex)
            {
                return BadRequest(new { error = ex.Message, innerError = ex.InnerException?.Message });
            }
        }

        // PUT: api/cleanup/5
        [HttpPut("{id}")]
        public async Task<IActionResult> UpdateCleanupRecord(int id, [FromBody] CleanupRecord record)
        {
            var userId = GetUserId();
            var existingRecord = await _context.CleanupRecords
                .FirstOrDefaultAsync(r => r.CleanupRecordId == id && r.UserId == userId);

            if (existingRecord == null)
            {
                return NotFound();
            }

            existingRecord.MWMonth = record.MWMonth;
            existingRecord.ApplicationName = record.ApplicationName;
            existingRecord.Assigned = record.Assigned;
            existingRecord.Go = record.Go;
            existingRecord.IfNoWhy = record.IfNoWhy;
            existingRecord.CCRChecked = record.CCRChecked;
            existingRecord.Bin2Prod = record.Bin2Prod;
            existingRecord.Config2Prod = record.Config2Prod;
            existingRecord.RDChecked = record.RDChecked;
            existingRecord.CFChecked = record.CFChecked;
            existingRecord.CheckedDate = record.CheckedDate;
            existingRecord.CCRNumber = record.CCRNumber;
            existingRecord.Jira = record.Jira;
            existingRecord.Repository = record.Repository;
            existingRecord.LASCODE02Path = record.LASCODE02Path;
            existingRecord.MovedToDoNotDeploy = record.MovedToDoNotDeploy;
            existingRecord.CommentsNotes = record.CommentsNotes;
            existingRecord.UpdatedAt = DateTime.UtcNow;

            await _context.SaveChangesAsync();

            return NoContent();
        }

        // DELETE: api/cleanup/5
        [HttpDelete("{id}")]
        public async Task<IActionResult> DeleteCleanupRecord(int id)
        {
            var userId = GetUserId();
            var record = await _context.CleanupRecords
                .FirstOrDefaultAsync(r => r.CleanupRecordId == id && r.UserId == userId);

            if (record == null)
            {
                return NotFound();
            }

            _context.CleanupRecords.Remove(record);
            await _context.SaveChangesAsync();

            return NoContent();
        }
    }
}

================================================================================

FILE: Controllers/DeploymentController.cs
================================================================================

using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using MWManagementAPI.Data;
using MWManagementAPI.Models;
using System.Security.Claims;

namespace MWManagementAPI.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    [Authorize]
    public class DeploymentController : ControllerBase
    {
        private readonly ApplicationDbContext _context;

        public DeploymentController(ApplicationDbContext context)
        {
            _context = context;
        }

        private int GetUserId()
        {
            var userIdClaim = User.FindFirst(ClaimTypes.NameIdentifier)?.Value;
            return int.Parse(userIdClaim);
        }

        // GET: api/deployment?mwMonth=January 2024
        [HttpGet]
        public async Task<ActionResult<IEnumerable<DeploymentRecord>>> GetDeploymentRecords([FromQuery] string mwMonth)
        {
            var userId = GetUserId();

            var records = await _context.DeploymentRecords
                .Where(r => r.UserId == userId && r.MWMonth == mwMonth)
                .OrderByDescending(r => r.CreatedAt)
                .ToListAsync();

            return Ok(records);
        }

        // GET: api/deployment/5
        [HttpGet("{id}")]
        public async Task<ActionResult<DeploymentRecord>> GetDeploymentRecord(int id)
        {
            var userId = GetUserId();
            var record = await _context.DeploymentRecords
                .FirstOrDefaultAsync(r => r.DeploymentRecordId == id && r.UserId == userId);

            if (record == null)
            {
                return NotFound();
            }

            return Ok(record);
        }

        // POST: api/deployment
        [HttpPost]
        public async Task<ActionResult<DeploymentRecord>> CreateDeploymentRecord([FromBody] DeploymentRecord record)
        {
            try
            {
                var userId = GetUserId();
                
                // Set user ID and timestamps
                record.UserId = userId;
                record.CreatedAt = DateTime.UtcNow;
                record.UpdatedAt = DateTime.UtcNow;
                
                // Validate required fields
                if (string.IsNullOrWhiteSpace(record.MWMonth) ||
                    string.IsNullOrWhiteSpace(record.ApplicationName) ||
                    string.IsNullOrWhiteSpace(record.Validated) ||
                    string.IsNullOrWhiteSpace(record.AssignedTo) ||
                    string.IsNullOrWhiteSpace(record.Environment) ||
                    string.IsNullOrWhiteSpace(record.ReleaseCreated) ||
                    string.IsNullOrWhiteSpace(record.ReleaseChecked) ||
                    string.IsNullOrWhiteSpace(record.Deployed))
                {
                    return BadRequest(new { error = "All required fields must be filled" });
                }

                _context.DeploymentRecords.Add(record);
                await _context.SaveChangesAsync();

                return CreatedAtAction(nameof(GetDeploymentRecord), new { id = record.DeploymentRecordId }, record);
            }
            catch (Exception ex)
            {
                return BadRequest(new { error = ex.Message, innerError = ex.InnerException?.Message });
            }
        }

        // PUT: api/deployment/5
        [HttpPut("{id}")]
        public async Task<IActionResult> UpdateDeploymentRecord(int id, [FromBody] DeploymentRecord record)
        {
            var userId = GetUserId();
            var existingRecord = await _context.DeploymentRecords
                .FirstOrDefaultAsync(r => r.DeploymentRecordId == id && r.UserId == userId);

            if (existingRecord == null)
            {
                return NotFound();
            }

            existingRecord.MWMonth = record.MWMonth;
            existingRecord.ApplicationName = record.ApplicationName;
            existingRecord.Validated = record.Validated;
            existingRecord.AssignedTo = record.AssignedTo;
            existingRecord.Environment = record.Environment;
            existingRecord.ReleaseCreated = record.ReleaseCreated;
            existingRecord.ReleaseChecked = record.ReleaseChecked;
            existingRecord.Deployed = record.Deployed;
            existingRecord.ReleaseURL = record.ReleaseURL;
            existingRecord.CommentsNotes = record.CommentsNotes;
            existingRecord.UpdatedAt = DateTime.UtcNow;

            await _context.SaveChangesAsync();

            return NoContent();
        }

        // DELETE: api/deployment/5
        [HttpDelete("{id}")]
        public async Task<IActionResult> DeleteDeploymentRecord(int id)
        {
            var userId = GetUserId();
            var record = await _context.DeploymentRecords
                .FirstOrDefaultAsync(r => r.DeploymentRecordId == id && r.UserId == userId);

            if (record == null)
            {
                return NotFound();
            }

            _context.DeploymentRecords.Remove(record);
            await _context.SaveChangesAsync();

            return NoContent();
        }
    }
}

================================================================================

FILE: MWManagementAPI.csproj
================================================================================

<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Authentication.JwtBearer" Version="8.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="8.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="8.0.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="8.0.0">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
    </PackageReference>
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />
  </ItemGroup>

</Project>

================================================================================

SETUP INSTRUCTIONS:
===================

1. CREATE THE PROJECT:
   dotnet new webapi -n MWManagementAPI
   cd MWManagementAPI

2. INSTALL REQUIRED PACKAGES:
   dotnet add package Microsoft.EntityFrameworkCore
   dotnet add package Microsoft.EntityFrameworkCore.SqlServer
   dotnet add package Microsoft.EntityFrameworkCore.Tools
   dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer

3. CREATE DATABASE:
   - Open SQL Server Management Studio
   - Run the SQL script provided above
   - Update connection string in appsettings.json with your server details

4. CREATE FOLDERS AND FILES:
   - Create folders: Controllers, Models, Data, Services
   - Copy all files from this document to their respective locations

5. RUN MIGRATIONS (if using Code-First approach):
   dotnet ef migrations add InitialCreate
   dotnet ef database update

6. RUN THE APPLICATION:
   dotnet run
   
   API will be available at: https://localhost:7204

7. TEST THE API:
   - Open browser: https://localhost:7204/swagger
   - Test endpoints using Swagger UI

8. UPDATE FRONTEND:
   - Update API_BASE_URL in your HTML file to match your API URL
   - Ensure CORS is properly configured

SECURITY NOTES:
===============
- Change the JWT SecretKey in appsettings.json to a secure random string
- Never commit appsettings.json with real credentials to source control
- Use environment variables for sensitive data in production
- Enable HTTPS in production
- Implement proper password hashing (consider using BCrypt instead of SHA256)

API ENDPOINTS:
==============

Authentication:
- POST /api/auth/register - Register new user
- POST /api/auth/login - Login user

Cleanup Records:
- GET /api/cleanup?mwMonth=January 2024 - Get all cleanup records for month
- GET /api/cleanup/{id} - Get specific cleanup record
- POST /api/cleanup - Create new cleanup record
- PUT /api/cleanup/{id} - Update cleanup record
- DELETE /api/cleanup/{id} - Delete cleanup record

Deployment Records:
- GET /api/deployment?mwMonth=January 2024 - Get all deployment records for month
- GET /api/deployment/{id} - Get specific deployment record
- POST /api/deployment - Create new deployment record
- PUT /api/deployment/{id} - Update deployment record
- DELETE /api/deployment/{id} - Delete deployment record

All endpoints except authentication require Bearer token in Authorization header.

================================================================================
END OF PROJECT FILES
================================================================================
`;

            const blob = new Blob([projectStructure], { type: 'text/plain' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'MWManagementAPI_Complete_Project.txt';
            document.body.appendChild(a);
            a.click();
            
            setTimeout(() => {
                window.URL.revokeObjectURL(url);
                document.body.removeChild(a);
                showMessage('✅ API project files downloaded successfully!', 'success');
            }, 100);
        }

        function showMessage(message, type) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${type}`;
            messageDiv.textContent = message;
            document.body.appendChild(messageDiv);
            
            setTimeout(() => {
                messageDiv.remove();
            }, 3000);
        }

        function showLoading(show) {
            const loading = document.getElementById('loading');
            if (show) {
                loading.classList.add('active');
            } else {
                loading.classList.remove('active');
            }
        }

        function escapeHtml(text) {
            const map = {
                '&': '&amp;',
                '<': '&lt;',
                '>': '&gt;',
                '"': '&quot;',
                "'": '&#039;'
            };
            return String(text).replace(/[&<>"']/g, m => map[m]);
        }
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9b7d48e1d7b5e9e1',t:'MTc2NzM4ODY2Mi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
