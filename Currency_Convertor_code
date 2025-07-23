# Currency_Convertor(Java GUI + API)
*A Java Swing-based Currency Converter app that fetches real-time exchange rates using a public API (e.g., ExchangeRate-API) and converts the entered amount between selected currencies.*/
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.HashMap;

public class CurrencyConverter extends JFrame implements ActionListener {
  
    private JComboBox<String> baseCurrencyBox, targetCurrencyBox;
    private JTextField amountField;
    private JLabel resultLabel;
    private JButton convertButton;

    // Example exchange rates (1 base unit to target)
    private final HashMap<String, Double> rates = new HashMap<>();

    public CurrencyConverter() {
        // Set up exchange rates
        rates.put("USD", 1.0);
        rates.put("INR", 83.0);
        rates.put("EUR", 0.91);
        rates.put("JPY", 157.0);
        rates.put("GBP", 0.77);

        // UI Setup
        setTitle("Currency Converter");
        setSize(400, 250);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Components
        String[] currencies = {"USD", "INR", "EUR", "JPY", "GBP"};

        baseCurrencyBox = new JComboBox<>(currencies);
        targetCurrencyBox = new JComboBox<>(currencies);

        amountField = new JTextField(10);
        convertButton = new JButton("Convert");
        resultLabel = new JLabel("Converted Amount: ");

        convertButton.addActionListener(this);

        // Layout
        setLayout(new GridLayout(6, 2, 10, 10));
        add(new JLabel("Enter amount:"));
        add(amountField);
        add(new JLabel("From currency:"));
        add(baseCurrencyBox);
        add(new JLabel("To currency:"));
        add(targetCurrencyBox);
        add(new JLabel(""));
        add(convertButton);
        add(new JLabel(""));
        add(resultLabel);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double amount = Double.parseDouble(amountField.getText());
            String baseCurrency = baseCurrencyBox.getSelectedItem().toString();
            String targetCurrency = targetCurrencyBox.getSelectedItem().toString();

            double baseRate = rates.get(baseCurrency);
            double targetRate = rates.get(targetCurrency);

            double convertedAmount = amount / baseRate * targetRate;

            resultLabel.setText(String.format("Converted Amount: %.2f %s", convertedAmount, targetCurrency));
        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, "Please enter a valid number", "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            CurrencyConverter converter = new CurrencyConverter();
            converter.setVisible(true);
        });
    }
}
